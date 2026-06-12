---
title: "Mono-based application packaging for Precise"
date: 2012-04-19
forum: Packaging and Compiling Programs
---

### Post by lubosh on 2012-04-19
Hi, I'm developing accounting software in C#. It works well under Ubuntu 11.10 since it comes with Mono pre-installed by default. All I'm distributing is single zipped binary exe file. So far all good.

However on Ubuntu 12.04 situation is a bit more complicated. Mono doesn't come by default, so users need to install it before using my app which is not particularly user-friendly.

What would be the simplest way that could possibly work? I would like to distribute this app through software center, ideally as a ZIP file. Is it possible to somehow indicate to software center my app depends on Mono?

---

### Post by sffvba[e0rt on 2012-04-19
If your application is a deb file then all of the dependencies would be calculated and installed when your app is installed AFAIK.


404

---

