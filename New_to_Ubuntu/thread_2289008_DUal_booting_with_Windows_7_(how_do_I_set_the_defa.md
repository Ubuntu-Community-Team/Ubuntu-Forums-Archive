---
title: "DUal booting with Windows 7 (how do I set the default OS to windows)"
date: 2015-07-31
forum: New to Ubuntu
---

### Post by Mugen_H on 2015-07-31
Hi guys, I just installed a dual boot with windows 7. Now I want to do two things. 

1) set the default OS to be windows 7 

I've googled around for this. The solution that people give applies till Ubuntu 13 (to install the SoftwareManager or something like that). However, Ubuntu 14 has "grub2" and I'm not finding any way to change the default OS in this grub 2 thing. Also, some people online were talking about changing some code in some file. I couldn't follow their instructions at all.


2) I would like to set a timeout value during OS selection to 3 seconds after which it should load the default OS. Currently it appears that there is no time out value.

Could someone please help me out on this in simple language please?

---

### Post by yancek on 2015-07-31
I don't know what you have been reading but Ubuntu has been using Grub2 since version 9.10.  You can change the default menuentry to boot as well as the timeout in the file /etc/default/grub.  If you open that file in a text editor with root privileges:  sudo gedit /etc/default/grub you should see the options shown below near the top of the file.  Change the GRUB_TIMEOUT to what you want.  The GRUB_DEFAULT will be a number.  When you boot, count down to the line with your windows entry and change the entry from "0".  In this instance, Grub counts from zero to if windows is the fourth entry, put a three. 

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

---

### Post by oldfred on 2015-07-31
You can use the number, but you can also use the description in grub menu. But it must be exact so copy & paste.

       # backup first
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
# copy from this file:
gedit /boot/grub/grub.cfg
# and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

You can also when editing change timeout from 10 to 3:
GRUB_TIMEOUT=10

---

### Post by Mugen_H on 2015-07-31
Done! It woiked like a charm! Thanks a load for your help dude!

---

