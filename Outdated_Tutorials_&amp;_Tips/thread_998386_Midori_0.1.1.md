---
title: "Midori 0.1.1"
date: 2008-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Stemp on 2008-11-30
Here it is : Midori 0.1.1 is out with WebKit 38850.

So grab the new version from the [webkit-team PPA]("https://launchpad.net/~webkit-team/+archive")

You’ll have to launch midori using this command :

WEBKIT_IGNORE_SSL_ERRORS="1" midori

You’ll also need **ca-certificates** package and sadly midori won’t work with self-certified site :(

But it’s still fast, lightweight, standard compliant (100% to acid3) and fun.

Thanks again to the upstream developpers and to the real packagers from Debian & Ubuntu

Links :

[Midori]("http://software.twotoasts.de/index.php?/pages/midori_summary.html")
[WebKit]("http://webkit.org/")
[Ubuntu webkit-team]("https://edge.launchpad.net/~webkit-team")
[XFCE Midori]("http://wiki.xfce.org/midori_faq")

---

### Post by d4v1dv00 on 2008-12-11
the command

```
WEBKIT_IGNORE_SSL_ERRORS="1" midori
```

does not work

---

### Post by Stemp on 2008-12-11
What do you mean by does not work ?

---

