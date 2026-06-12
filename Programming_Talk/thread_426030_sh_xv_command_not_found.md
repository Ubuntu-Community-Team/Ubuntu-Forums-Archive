---
title: "sh: xv: command not found"
date: 2007-04-28
forum: Programming Talk
---

### Post by maforast on 2007-04-28
Hi I have a problem when i try to lunch a python program to process some images. I've installed libxv.dev libxvmc.dev but nothing to do I have same error yet on terminal
sh: xv: command not found

Can u help me may be i have to install another program to fix error

tnx in advance

---

### Post by kano on 2007-04-30
After some searching, it seems that xv isn't part of any the ubuntu repos (licensing issues i guess?)

This guide shows you have to build a debian package for xv.
[http://bok.fas.harvard.edu/debian/xv/index.html](http://bok.fas.harvard.edu/debian/xv/index.html)

the only library I needed to install to be able to build the package for me was libtiff4-dev.

i've attached the xv deb that i built, but the xv-docs package was just a little to big to attach... if you need the docs package and don't want to build the packages yourself, lemme know and I'll upload it somewhere for you to download :)

(this was built on feisty btw... not sure if it'll work for older versions of ubuntu. if you're using an older version and it doesnt, you'll have to follow instructions i linked >.<)

---

