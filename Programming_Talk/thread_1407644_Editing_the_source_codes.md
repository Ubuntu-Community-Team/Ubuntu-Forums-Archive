---
title: "Editing the source codes"
date: 2010-02-15
forum: Programming Talk
---

### Post by eklavya_18 on 2010-02-15
Open source impresses me a lot. I have C and Java in course curriculum. I use Ubuntu9.10. I would like to start editing the source code or for that matter atleast start reading them. But, I have no idea where to start from? Help

---

### Post by Zugzwang on 2010-02-15
Ubuntu is a Linux distribution that consists of a lot of packages. The packages contain programs which in turn have source codes. So in order to edit the source code for "Ubuntu 9.10", you first need to pick a package you want to change and then download its source using: ```
apt-get source <packagename>
``` All packages have individual source codes, so there's no way to download *the* source code for Ubuntu.

---

### Post by CptPicard on 2010-02-15
In console,

```

apt-get source some-package-name-here

```

Will pull the source to the given package for your inspection...

---

### Post by eklavya_18 on 2010-02-15
Hey thanx.Can you suggest any package which is really small? You know I want something with very limited number of programs and which is easy  to understand.

---

### Post by nvteighen on 2010-02-15
> **eklavya_18 said:**
> Hey thanx.Can you suggest any package which is really small? You know I want something with very limited number of programs and which is easy  to understand.

Ugh... the most simple thing I've seen maybe nano... Even very 'simple' things like the less pager have a reasonable amount of code in it...

Maybe take the source for gnu-utils, binutils, bsdutils and similar and look at each utility's source?

---

