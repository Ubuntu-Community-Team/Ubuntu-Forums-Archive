---
title: "GRUB4DOS When trying to boot into Ubuntu."
date: 2013-06-03
forum: New to Ubuntu
---

### Post by Zenithex on 2013-06-03
First off I'm sorry if this is a common post, but I couldn't find it...

Yesterday I tried to set up my Windows 8 PC to dual boot into Ubuntu, I followed a guide (couldn't find the exact one again) did everything exactly as the guide said, but it is just giving me this screen when I try to boot into Ubuntu
[IMG]http://i.stack.imgur.com/mvBt3.jpg[/IMG]
(Sorry I dont know how to re-size the image)

I am really confused as I have never used Linux or Ubuntu before, I did try to do the whole procedure again but I got to the exact same screen. 

Sorry for the terrible post but I have never used forums before.
Thanks for any help.

---

### Post by Mark Phelps on 2013-06-03
GRUB4DOS is installed as a byproduct of trying to install using WUBI -- which, as far as I know, doesn't work with Win8.  But, I don't personally use it.

---

### Post by Zenithex on 2013-06-03
Any alternatives I can use?

---

### Post by Mark Phelps on 2013-06-03
> **Zenithex said:**
> Any alternatives I can use?

Yes ... you should consider a traditional dual-boot installation.  

First thing you need to do is go into Win8 and REMOVE the Ubuntu installation.

You probably have UEFI BIOS and maybe, secure-boot as well.  There are other folks on the forums that specialize in dealing with those.  You need to wait until they respond.  Rushing in prematurely can easily break Win8 and render it unbootable.

---

### Post by Zenithex on 2013-06-03
Thanks, will try that.

---

### Post by bcbc on 2013-06-04
GRUB4DOS (part of it) is used with Wubi, but not the part shown in that image. Whatever instructions you followed are not correct and likely installed the actual GRUB4DOS and not the part that Wubi uses.

I doubt you have UEFI because GRUB4DOS wouldn't have been able to run, and most likely you wouldn't have even got a grub> prompt.

---

