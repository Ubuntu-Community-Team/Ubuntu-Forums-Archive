---
title: "How to access usb drive with zenwalk??"
date: 2008-12-13
forum: Other OS Talk
---

### Post by rixtr66 on 2008-12-13
ubuntu is my main os,but i like to fiddle with other linux distros!
I have zenwalk on my usb drive.i have the correct grub entry to access it.
however i get a kernel panick,im thinking changing the timeout to 10 or 11 sec.may solve this problem.But i dont know how to access the lilo.conf to change it!someone showed me a way to boot it but it didnt work.zenwalk has an initrid but since its lilo im running a chainloader.anyway running stuff on a usb drive is a pain!but i like the challenge.so can anyone help me?
it would be much appreciated!
Rick

---

### Post by Titan8990 on 2008-12-13
IMO I think you will have much better luck from doing that kind of stuff from a virtual machine. Then you also kill 2 birds with one stone, learn VM technology and learn Zenwalk/Slackware.

---

### Post by bodhi.zazen on 2008-12-13
First, although Zenwalk uses LILO by default, you can boot it with grub.

I do not know if the problem is that you are chainloading lilo or if the kernel or initrd you have does not support your usb drive.

I suggest you install grub into the usb drive (Zenwalk partition).

See this :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

