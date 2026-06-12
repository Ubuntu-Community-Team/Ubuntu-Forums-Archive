---
title: "Duel Partitioned Windows Updating Problems"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by Wolffee on 2012-11-06
Hey guys,

You all have always been amazing help to me in the past and I find myself needing your assistance again. I have a dual partitioned system with Ubuntu 12.04 and Win 7. My system runs fine except when windows needs to update. I dual partitioned it myself so I didn't know until afterwards that if grub 2 is your main booter that windows doesn't really know where to install it's updates. That is at least what I've read online. I'm here asking if you guys know a way to make windows my main booter without redoing the whole partitioning process or losing my data or ******* up grub 2. I don't know that much about what I'm saying right now, and I'll totally admit that. But y'alls help I've been able to figure things out in the past. Any advice on this problem would be greatly appreciated. It's getting kind of ridiculous, every time windows tries to update I have to restore it to before the update or it blue screens. 
--Ty

---

### Post by PinkFloyd102489 on 2012-11-06
You can download a program called EasyBCD that will allow you to restore the default Windows bootloader and also allow you to chainload your Ubuntu installation from the Windows bootloader.

It will function the same way as GRUB, except it's the Windows bootloader.

---

### Post by Wolffee on 2012-11-06
Thank you! Is there anything specific I should know before I do this?

---

### Post by PinkFloyd102489 on 2012-11-06
[http://www.ubuntugeek.com/use-the-windows-bootloader-to-dual-boot-windows-vista-and-ubuntu.html]("http://www.ubuntugeek.com/use-the-windows-bootloader-to-dual-boot-windows-vista-and-ubuntu.html")

---

### Post by Wolffee on 2012-11-06
I followed all the steps in that article and it worked, mostly. EasyBCD is now the booter for my system and it boots linux and windows just fine. But I think something went awry when I changed it so that grub 2's loading time was 0 as opposed to 10 seconds. Now grub loads the ubuntu login screen, I enter my password and it just loads the login screen again. If I could get into ubuntu I would just change it back so that grub loads and I just have to click through two booters, which isn't a big deal to me. But I don't know how to fix this. Any advice?

---

