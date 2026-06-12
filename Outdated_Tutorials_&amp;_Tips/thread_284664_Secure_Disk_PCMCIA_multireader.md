---
title: "Secure Disk PCMCIA multireader"
date: 2006-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by rioguia on 2006-10-25
[I]Secure Disk PCMCIA multireader
Adding a Secure Disk PCMCIA multireader to a laptop running Ubuntu.  You should be able to just cut and paste the lines without italic fonts into a terminal/editor and get a good result on most laptops with a basic setup.  This exercise assumes you have gedit, but you could easily substitute vi, pico, joe, emacs or your other favorite editor.[/I]

*1. * 
sudo gedit /etc/fstab

*2.  add the following line at the end of the file* 
/dev/hde1 /media/sd vfat noauto,rw,user,exec, 0 0

*3.  *
sudo mkdir /media/sd

*4.  **You should now be able to mount the new directory and browse to the folder*
mount /media/sd
cd /media/sd

---

