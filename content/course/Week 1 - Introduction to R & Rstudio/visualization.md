---
title: Students - Enter the Tidyverse
date: '2021-01-01'
type: book
weight: 30
highlight: true
---

The tidyverse is a series of `packages` that enhance the capabilities of base R. 

<!--more-->

{{< icon name="clock" pack="fas" >}} As much time as you want - it's nearly endless!

Base R is powerful, but is expanded through the use of **packages**. Packages, are created by R users to do a specific set of things, ie graphing or machine learning. Several of the most popular packages that we will use in this course are part of the [Tidyverse](https://www.tidyverse.org/packages/). 

## Video Tutorial

{{< youtube q0uGggl3RbM >}}

## Quiz

{{< spoiler text="What are packages?" >}}
Packages are a collection of code that expands the capabilities of base R in various ways.  
{{< /spoiler >}}

{{< spoiler text="How do you install packages in RStudio?" >}}

``` {r}
# first we need to install the package
install.packages("ggplot2")
# once the package is installed we then need to load it
library(ggplot2)
# now we can use the package
set.seed(1)
df <- data.frame(
  gp = factor(rep(letters[1:3], each = 10)),
  y = rnorm(30)
)
ds <- do.call(rbind, lapply(split(df, df$gp), function(d) {
  data.frame(mean = mean(d$y), sd = sd(d$y), gp = d$gp)
}))

# The summary data frame ds is used to plot larger red points on top
# of the raw data. Note that we don't need to supply `data` or `mapping`
# in each layer because the defaults from ggplot() are used.
myGraph <- ggplot(df, aes(gp, y)) +
  geom_point() +
  geom_point(data = ds, aes(y = mean), colour = 'red', size = 3)
# the graph can then be loaded by calling the myGraph object
myGraph

```
{{< figure src="exampleplot.png" caption="A caption" numbered="true" >}} 

{{< /spoiler >}}
