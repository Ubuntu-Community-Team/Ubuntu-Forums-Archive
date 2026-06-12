---
title: "[SOLVED] Adobe"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by sprogmeister on 2008-06-18
I am using Hardy Heron but have found a need to still use XP:(. I have a pdf file that, when open with adobe reader in XP, allows information to be typed into it. I have tried to use Open Office and download adobe for Hardy Heron, but to no avail! Can anyone help?

---

### Post by dracayr on 2008-06-18
hi,

try the foxit reader:
[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

EDIT: I just saw that foxit reader doesn't work in ubuntu. but you can use wine:
[http://sodeve.net/foxit-reader-on-ubuntu-linux-through-wine/](http://sodeve.net/foxit-reader-on-ubuntu-linux-through-wine/)

dracayr

---

### Post by stchman on 2008-06-18
> **sprogmeister said:**
> I am using Hardy Heron but have found a need to still use XP:(. I have a pdf file that, when open with adobe reader in XP, allows information to be typed into it. I have tried to use Open Office and download adobe for Hardy Heron, but to no avail! Can anyone help?

Acrobat reader 8 can be installed via the Medibuntu repos.

To install the Medibuntu repo do this.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Follow the first part on installing the Medibuntu repo in Hardy.

Next do this in a terminal:

```
sudo apt-get update
sudo apt-get install acroread
```

Acrobat reader 8 will be installed.

---

### Post by sprogmeister on 2008-06-19
Thanks for your help. All's well and working!

---

### Post by sprogmeister on 2008-06-19
Although, having said that, how do you add the plug-ins. Thanks for all the help

---

### Post by redbob on 2008-06-19
I made a test with a PDF form with Evince, and I could fill the form like a charm, so I didn't see utility to use Adobe or FoxIt.

---

