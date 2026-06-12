---
title: "Grub error 15 -- New install"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Bodsda on 2008-06-10
Hi, I've been using Ubuntu for about 6 months now and had a stable install of Hardy. I thought now that i felt confident enough to reinstall to clear out the junk and fix a few mistakes i'd made. I initially had all my Ubuntu stuff on 1 hard drive, i also dual boot with Windows xp  on a seperate drive. This time round i put / and swap on a 120gb ide drive, and had /home on its own on a 80gig sata drive. Windows is on a 40gb ide drive. The install went fine but when i rebooted i got 

grub error 15

which is cannot locate file stage1.5 in my case. I checked my /boot/grub and sure enough there is no stage1.5, how can i get one?

Also every now and again my hard drives decide to reorder themselves which makes fixing grub a real pain. I was told to make udev rules for 
this prob but i have no idea how. 

Anyone know how to fix either issue?

sudo fdisk -l
[http://pastebin.com/f5fcdbb0d]("http://pastebin.com/f5fcdbb0d")

ls of my /boot/grub on sdc1
[http://pastebin.com/f7882f449]("http://pastebin.com/f7882f449")

ls of my /boot on sdc1
[http://pastebin.com/f1de7ea3]("http://pastebin.com/f1de7ea3")

If you need any other info plz ask.

Thanks in advanced
Bodsda

---

### Post by Duck2006 on 2008-06-10
Some grub reading that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

