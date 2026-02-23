# Tokenization Efficiency and Multilingual Cost in Large Language Models

## Overview

Large language models process text as tokens rather than characters. Because tokenization is not uniform across languages, semantically equivalent text can require very different numbers of tokens. This project analyzes how tokenization efficiency varies across English, Spanish, Hindi, and Chinese, and examines the implications for context window limits and token-based pricing in multilingual LLM systems.

## Methods

This project uses a controlled parallel corpus containing 25 semantically comparable texts in each language, including short user-facing prompts, technical statements, and longer explanatory paragraphs. All text is tokenized using the cl100k_base encoding from the tiktoken library to ensure consistency across languages.

For each language, the analysis computes:

Mean tokens per sample
Tokens per character
Characters per token (compression efficiency)
Tokens per 1,000 characters (cost proxy)
Approximate number of characters that fit in an 8,000-token context window

Distributions are visualized using bar charts and boxplots to show both central tendency and variability. A token-level inspection is included to illustrate how subword segmentation differs across scripts.

These methods were chosen to isolate tokenization effects while controlling for semantic content, allowing differences to be attributed primarily to tokenizer behavior and writing system characteristics.

## Key Results

Tokenization efficiency differs substantially across languages. English and Spanish are more compact under the selected tokenizer, fitting significantly more characters into a fixed 8k-token context window. Chinese and Hindi require more tokens for comparable content, reducing effective context capacity and increasing token-based cost per character.

These findings suggest that fixed token limits and token-based pricing create unequal effective context sizes across languages. While model architectures may be language-agnostic, tokenization introduces structural differ

## Requirements

Python 3.10+
pandas
matplotlib
tiktoken