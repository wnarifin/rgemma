# rgemma

<!-- commented out for parts I don't use -->
<!-- badges: start -->
<!--
[![CRAN status badge](https://www.r-pkg.org/badges/version/gemini.R)](https://CRAN.R-project.org/package=gemini.R)
[![CRAN downloads badge](https://cranlogs.r-pkg.org/badges/gemini.R)](https://cran.r-project.org/package=gemini.R)
![r-hub](https://github.com/jhk0530/gemini.R/actions/workflows/rhub.yaml/badge.svg)
[![gemini.R status badge](https://jhk0530.r-universe.dev/badges/gemini.R)](https://jhk0530.r-universe.dev/gemini.R)
-->

<!-- badges: end -->

R package to use Google's gemma (and gemini) via API on R.

## Acknowledgment
This package was modified from gemini.R [https://jhk0530.github.io/gemini.R/]. I thank the original author for the wonderful package.

This is a customized fork, combining both gemma and gemini in generic functions. The original author of gemini.R has also added separate gemma_* functions for using gemma. So, this fork attempts to keep the functions simple, providing functions that work for both gemma and gemini.

Take note that many parts of the original package are still not modified. These are the parts (from which the functions come from) that work:

- `gemini.R`
- `gemini_chat.R`
- `gemini_image.R`

## Installation

#### From Github

```r
# install.packages("pak")
pak::pak("wnarifin/rgemma")
```

## Usage

```r
library(rgemma)

api_key = readLines("api_key") # from "api_key"" text file in your local folder
setAPI(api_key)
model = "gemma-3-27b-it"  # may change to gemma-* and gemini-* models

# gemini text ----
query = "What makes chilli spicy and hot?"
gemini(query, model) -> answer
answer |> cat()

# gemini chat ----
query1 = "What makes chilli spicy and hot?"
gemini_chat(query1, model = model) -> chat
chat$outputs |> cat()
query11 = "Summarize what you've said."
gemini_chat(query11, model = model, history = chat$history) -> chat
chat$outputs |> cat()

# gemini image ----
img = system.file("data/handful.png", package = "rgemma") # find in package folder
gemini_image(img, model = model) -> img_answer
img_answer |> cat()
```
