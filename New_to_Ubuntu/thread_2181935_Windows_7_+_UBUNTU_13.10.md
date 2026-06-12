---
title: "Windows 7 + UBUNTU 13.10"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by edu4rd on 2013-10-19
Hi guys ,

I want to ask you something : is it possible to have "normal" dual boot between windows 7 with the system partition drive encrypted with TrueCrypt  and ubuntu ?
The thing is i want to install ubuntu on another partition but i`m sure it will affect my boot system .

Shoud I 1st decrypt the sytem partition and then install ubuntu and after everything is ok with the dual boot , i shoud encrypt again the windows system partition ?

Did anyone tried that before ?
Any hints ?


Thanks .
(i`ve searched in others threads but didnt find what i was looking for.)

---

### Post by newb85 on 2013-10-19
From this thread [http://ubuntuforums.org/showthread.php?t=1559318](http://ubuntuforums.org/showthread.php?t=1559318) it looks like you should simply install Ubuntu and tell it to install GRUB to the Ubuntu partition rather than the boot partition.  Then when prompted for your Windows password you can hit Esc to get to GRUB to boot Ubuntu.  (I can't personally attest to this, and I'd recommend you do a little more reading.)

---

### Post by edu4rd on 2013-10-19
I`ve tried that with linux mint and didnt work and when i say didnt work ...i couldnt login on windows again because after i pressed ESC  a file was missing .tried to repair the mbr but no succes .
Thanks you .

---

