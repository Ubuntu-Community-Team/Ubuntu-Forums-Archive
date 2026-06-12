---
title: "[SOLVED] What are gtk2 development libraries?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-06-25
I am trying to compile Webkit into Epiphany using [this]("http://fosswire.com/2007/12/02/compile-epiphany-from-source-to-use-webkit/") guide. When trying to compile WebKit I run into an error ```
checking for WEBKITDEPS... configure: error: Package requirements (gtk+-2.0 >= 2.8
                  pango >= 1.0
                  cairo >= 1.4
                  libxml-2.0 >= 2.6) were not met:

No package 'gtk+-2.0' found
No package 'pango' found
No package 'cairo' found

``` and I read [here]("http://ubuntuforums.org/showthread.php?t=642253") that I need gtk2 dev libs. So what are the packages that I need?

---

### Post by mali2297 on 2008-06-25
Try installing **libgtk2.0-dev**, **libpango1.0-dev**, **libcairo2-dev** and **libxml2-dev**.

---

