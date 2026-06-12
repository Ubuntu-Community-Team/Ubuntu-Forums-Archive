---
title: "how to mass search through folders for specific files"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-01-04
Hey.

I just retrieved some data that was in my deleted partition. I've been left with 755 folders mainly full of junk. I'm specifically searching for .zip .odt .doc and .cbz files.
Is there any way to do this quickly and efficiently without having to go folder by folder? 

Cheers.

K.m

---

### Post by steeldriver on 2013-01-04
Hi there are some GUI tools (including maybe the dash search) but if you want to do it from the terminal, the 'find' command should be able to do that, e.g.

```
find */path/to/dir* -iname '*.zip' -o -iname '*.odt' -o -iname '*.doc' -o -iname '*.cbz'
```You can replace */path/to/dir* with . (dot) if you want to search from the current directory down

---

### Post by kabukiM0n0 on 2013-01-06
> **steeldriver said:**
> Hi there are some GUI tools (including maybe the dash search) but if you want to do it from the terminal, the 'find' command should be able to do that, e.g.

```
find */path/to/dir* -iname '*.zip' -o -iname '*.odt' -o -iname '*.doc' -o -iname '*.cbz'
```You can replace */path/to/dir* with . (dot) if you want to search from the current directory down


cheers! It also worked by just typing .zip .odt etc in the windows search bar.

---

