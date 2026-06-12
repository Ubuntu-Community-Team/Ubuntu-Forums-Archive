---
title: "python-pandas"
date: 2012-09-12
forum: Repositories &amp; Backports
---

### Post by onebir on 2012-09-12
This is a very useful package for time-series manipulation, which is under constant development.

It's difficult to install the dependencies (particularly scipy and numexpr). And the Ubuntu 12.04 repo's only include pandas 0.7.1, which lacks some useful features available in 0.8.1 (0.9.1 is in active development)

But the 12.10 repos include pandas 0.8.1. Since 12.04 is an LTS, shouldn't this be backported? Is there an appropriate place to request this?

And the neurodebian project has prepared binaries for pandas 0.8.1 for ubuntu 12.04:
[http://neuro.debian.net/pkgs/python-pandas.html#pkg-python-pandas](http://neuro.debian.net/pkgs/python-pandas.html#pkg-python-pandas)
and backported what appear to be the most up to date versions possible to ubuntu releases back to 8.04:
[http://neuro.debian.net/index.html#how-to-use-this-repository](http://neuro.debian.net/index.html#how-to-use-this-repository)

I was able to install pandas 0.8.1 easily when I finally discovered this. But neurodebian's support for ubuntu doesn't seem well-known, and quite likely some package maintenance work is being duplicated...

---

