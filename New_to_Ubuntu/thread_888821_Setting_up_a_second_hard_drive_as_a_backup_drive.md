---
title: "Setting up a second hard drive as a backup drive"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by macanliegh on 2008-08-13
I'm new to Ubuntu and just recently installed it on a 240 gigabyte SATA hard drive. It's working fine, but I would like to use an 80 gigabyte hard drive to store backup information and a copy of the system just in case. 

I was able to partition the second hard drive to ext3 using gparted, but what do I do next? 

How can I copy my files on the first drive onto the second? 

Also how do I fix the start up so that it correctly boots from the first drive? 

Thank you very much

---

### Post by bdfoster on 2008-08-13
> **macanliegh said:**
> I'm new to Ubuntu and just recently installed it on a 240 gigabyte SATA hard drive. It's working fine, but I would like to use an 80 gigabyte hard drive to store backup information and a copy of the system just in case. 

I was able to partition the second hard drive to ext3 using gparted, but what do I do next? 

How can I copy my files on the first drive onto the second? 

Also how do I fix the start up so that it correctly boots from the first drive? 

Thank you very much

It should just be copy/paste right? Mount the drives from the Places menu.

EDIT: When you go to your BIOS/CMOS, you have to change the boot order. When you start up, you should press something like Esc, F10, F12, etc. It should say at the bottom of the screen at some point in the beginning of the boot. Enter setup, then find something that says Boot Order or something to that effect. Make sure that it goes something like this...

1st: CD/DVD Drive
2nd: 1st Hard Drive
3rd: Floppy

and if there is a fourth...

4th: 2nd Hard Drive

If you have multiple optical drives, it is recommended that you put those first before any hard drives. I always put the Floppy Drive last but that is only because... I don't have one, and they aren't used really except for Win98 Boot Floppies.

---

### Post by mykyi on 2008-08-13
If you need help with mounting. Use 

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

It's step by step and helped me out alot.

Good luck!

---

### Post by Riffer on 2008-08-13
It shouldn't boot from your backup HD, as its doesn't have an OS on it thats bootable.

In order to copy files over, you may have to mount it and then enable shares.  You would do this by using the command in your terminal

gksudo nautilus

You have to supply your password at the prompt and it will then open up your file manager (nautilus) in superuser mode.

In the left hand column go to filesystem, in the new window find and go to the folder marked "media"   ) and in there you will see your HD's.  If you right click on your back up HD a context menu will come up, at the bottom is properties, click on that.  In that menu is several tabs, go to the one marked "share" in there clink the radio button for sharing your HD.  Also in the menu with the tabs is one marked permissions thats where you would go to change the permissions for that HD.  At this point I wouldn't change them though.

Hope this helps.

---

### Post by Elfy on 2008-08-13
>  but what do I do next?with regard to what exactly - you want it to mount only when you need, mount at boot automatically? If it was mounted you could set up backups for your /home or other at intervals.

> How can I copy my files on the first drive onto the second?Do you want a static copy? [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by eldragon on 2008-08-13
i use an external HDD where i backup my documents, my mails and the system's configurations nightly, incrementaly, and automatically.

i use rsnapshot. its an easy to configure script. i dont actually bother with backing up the entire system, since installing it isnt that much of a hassle.

rsnapshot isnt that hard to setup, reading its man pages is enough.
for automated backups, setup a cronjob (man crontab)

if you need some extra help, just drop a message and will try my best to help :D

good luck

---

### Post by macanliegh on 2008-08-13
Thanks a lot!

I went to the BIOS and for some reason the second hard drive was set as the primary boot device, so I set my cd/dvd drives and my primary hard drive as the first boot devices. 

Those mounting instructions were great, now I can copy paste files into my new /storage directory

Thanks a lot, I've been messing around for a couple of days trying to find the answer on the forums, and you were able to answer in a couple of hours! That's great!

---

