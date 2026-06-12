---
title: "Can Anyone tell a newbee how to repair the bootloader?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Lt.seahawk1 on 2008-07-20
I cannot see my Wndows Xp Pro partition. I think it's because grub loaded in my windows partition. How do I check. I can only boot with Ubuntu and want to go back my previous dual boot system till I become proficient with Ubuntu.Thanks in advance for your help.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by koji042 on 2008-07-20
You might want to look into the Super Grub Disk: [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/") I've never used it myself, but I've heard that others have used it to fix GRUB.

Hope that helps.

---

### Post by jonabyte on 2008-07-20
Check the /boot/grub/menu.lst file and see if windows is listed.
You'll need to know where it is installed i.e. hd(0,0), etc. and add it to the list if not.

---

### Post by bprof on 2008-07-20
I ran into a similar problem and I was able to solve it using EasyBCD. It allows you to configure bootloader and grub using GUI and allow you to select which system you want to use after reboot. Hope it will help you like it helped me.

---

### Post by arpanaut on 2008-07-20
This is a link to probably the most comprehensive information on grub out there.
You'll find link there for SuperGrub disk... sure fire boot disk and grub repair tool.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This is the Ubuntu Community Documentation.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

It's a lot of information to digest but if you become familiar with these pages you will never be stuck again.

Good Luck!

---

### Post by bumanie on 2008-07-20
Post output of > sudo fdisk -l > cat /boot/grub/menu.lst

---

### Post by jeffinhedon on 2008-07-22
Greetings and I hope this may be of use?
Check the repositories 
Run Synaptic Package Manager 
Search for grubed
There are two versions listed 
I installed the Kgrubeditor
I worked fine for me
I needed to remove various corrupted entry versions from the grub list 
This little prog allowed me to modify the list as required
It now looks a lot shorter and easier to use
BTW I have
XP
SUSE 10
and Ubuntu 8.04
So there you have it
Cheers:guitar:

---

