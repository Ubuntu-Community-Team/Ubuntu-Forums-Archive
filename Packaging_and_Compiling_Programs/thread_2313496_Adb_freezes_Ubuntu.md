---
title: "Adb freezes Ubuntu"
date: 2016-02-13
forum: Packaging and Compiling Programs
---

### Post by mikhail18 on 2016-02-13
I have Ubuntu 14.04 Lts. Any manipulation with Adb (Android debug bridge) freezes it forever:  opening android manager at AndroidStudio, using command "adb devices" at  terminal. Even if I want to reinstall android tools, using SDK manager  at android studio it turns my laptop to frozen batch, because firstly it  has to turn off Adb.

(Acer Aspire ES1-111)

---

### Post by raphael17 on 2016-04-27
Hello,

Exact same problem for me on Ubuntu 16.04 on a HP laptop. Did you find any solution ?

Regards

---

### Post by george126 on 2016-10-24
Hello, 
still havn't faound solution?, it seems like nobody even cares, has anyone tried downgrading kernel, saw a post that said that, guess im going to try that, im feeling desperate 

im on Xubuntu 16.04, and had the problem in ubuntu 16.04, gnome 16.04 as well

---

### Post by felipe28 on 2016-11-24
Hi,

I've been struggling with this problem since installed 16.04 and I've just found a solution now using 16.10.

I changed these options on my BIOS:

- From Legacy to UEFI boot
- Disabled USB 3.0 legacy

For some reason I altered these when I just bought my laptop (HP), but now I've restored them to default and adb is not freezing ubuntu anymore.
Greets

---

