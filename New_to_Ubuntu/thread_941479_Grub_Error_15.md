---
title: "Grub Error 15"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Igniteflow on 2008-10-08
I recently did a full reinstall, partitioning my 500GB drive as follows:
/dev/sda1 78.13 GB Vista (installed first)
/dev/sda2 13.97 GB Ubuntu /root (installed second)
/dev/sda3 465.52 GB Ubuntu /home

Problem is now when I boot up my comp, it just hangs at with a GRUB Error 15 message.  I've tried booting with a LiveCD and doing the **sudo grub, find /boot/grub/stage1, root (hd_,_), setup (hd0), quit** method which has worked for me in the past, but it isn't helping this time.
When I boot with the Alternate CD and select Boot from First Hard Disk it works so I know I'm close, but it's really not an ideal setup to leave things like that.  Any suggestions would be hugely appreciated.

---

### Post by muteXe on 2008-10-08
Dunno if this will help, but check out supergrub disk:
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by Igniteflow on 2008-10-08
The problem is fixed now.  I wish I could tell you exactly how I did it, but I've been trying so many things I'm not sure what actually did it.  I need to get more methodical.  For anyone experiencing similar problems though, check out the [GRUB homepage]("http://users.bigpond.net.au/hermanzone/p15.htm") It has tons of really useful information and goes into much more detail on GRUB than you'll find on the forums.

Don't forget when editing /boot/grub/menu.lst that GRUB counts drives from zero, so:
/dev/sda1 becomes (hd0,0) 
/dev/sda2 becomes (hd0,1)
/dev/sdb1 becomes (hd1,0)
/dev/sdb2 becomes (hd1,1)
Lastly, always make a backup of menu.lst, it might just save you a lot of time.

---

### Post by Malta paul on 2008-10-08
Hi, Grub doesn't know where you mast boot record is. When you get to the Grub menu try 'E' Edit and change 1,0 or 0,1 till you find it. I would use the 'recovery mode' to see what happens during boot-up. 
No setting this way will be saved to your Boot Menu. This can be changed when you have booted successfully!. (sorry I am at work at the moment so not using Ubuntu,) Will send more details when I get home if you require.

---

