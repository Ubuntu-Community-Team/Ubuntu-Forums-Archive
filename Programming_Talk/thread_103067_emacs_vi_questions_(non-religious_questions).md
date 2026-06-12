---
title: "emacs vi questions (non-religious questions)"
date: 2005-12-13
forum: Programming Talk
---

### Post by frootstripe on 2005-12-13
Hi,

I've installed Kubuntu 3.10 and was wondering what packages I want to apt-get to get the macros for python on both emacs and vi. Would also like to produce latex and docbook sgml files.

---

### Post by toojays on 2005-12-13
My answers are for emacs, which is my editor of choice. For python, install python-mode. Emacs comes with a basic LaTeX mode, but the auctex mode is highly recommended for advanced LaTeX use. For sgml files, install the psgml package. If you ever use DocBook XML, I highly recommend the nxml-mode package.

---

### Post by hod139 on 2005-12-14
[QUOTE=frootstripe]Hi,

I've installed Kubuntu 3.10 and was wondering what packages I want to apt-get to get the macros for python on both emacs and vi. Would also like to produce latex and docbook sgml files.[/QUOTE]

For latex you need to install tetex-base and probably want to install tetex-extra.
```

sudo apt-get install tetex-base tetex-extra

```
The tetex-extra package contains many of the useful latex styles (like amstex) you will most likely need.

---

