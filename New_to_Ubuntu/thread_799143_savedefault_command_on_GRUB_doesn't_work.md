---
title: "savedefault command on GRUB doesn't work"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by noorez on 2008-05-18
The savedefault command on GRUB doesn't seem to work. I get an error 21 unrecognized command. I did a bit of searching and found that this might be a bug but I was wondering if anyone here found a fix or a workaround?

---

### Post by spiderbatdad on 2008-05-18
can you post how you edited the file?
```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

``` Should look like the above example. ## are comments in /grub/menu.lst.
Single(#) are directives and should be left in place.
> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##

---

