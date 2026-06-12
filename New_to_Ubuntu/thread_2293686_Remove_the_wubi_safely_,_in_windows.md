---
title: "Remove the wubi safely , in windows"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by joseph68 on 2015-09-06
I have Wubi files. some Dll, in old windows files after installing  Windows 10 and need to safely remove them and am looking for some help.  Very new to Ubuntu but I like it so much am considering installing it  permanently. The problem with the wubi files is that when the Ubuntu  boot fix disc was ran it warned of broken wubi and Ive been stuck in the  windows 10 boot loop. If it wasn't for the Ubuntu usb flash drive I'd  be in big trouble Included a photo. Please help, ive installed windows 10, 1 too many times and am afraid to restart my machine. Thank you

---

### Post by yancek on 2015-09-06
Use the wubi site at ubuntu.com at the link below.  Scroll down the page and there you will see explicit instructions on how to uninstall the program.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by tristan16 on 2015-09-07
WUBI isn't technically supported anymore, so you'd be better off with a dual-boot anyway. It's supported on 12.04, which means it'll be around until April of 2017, but everything I've seen basically says don't use it and don't tell others to use it.

---

### Post by hakuna_matata on 2015-09-07
> **joseph68 said:**
> I have Wubi files. some Dll, in old windows files after installing  Windows 10 and need to safely remove them and am looking for some.
IMHO there are files for different Wubis. Files and folders like Windows\WinSxS\amd64_microsoft-windows-d..se-wubids-datafiles* are for [Wubi]("https://en.wikipedia.org/wiki/Wubi_method"), a Chinese character input method.

Only wubildr and wubildr.mbr are files for [Wubi]("https://wiki.ubuntu.com/WubiGuide")!

---

