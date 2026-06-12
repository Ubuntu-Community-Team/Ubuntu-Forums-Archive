---
title: "Installing 12.04 lts and everytime it installes the screen fuzzes up"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Deaf Smith on 2014-05-30
Yes fuzzes up, mouse disapears, and nada.. can't do anything.

Right now I am on the 'try it' part of the cd and it works, but when I install it doen't.

I suspect the background image is not right for this HP screen (and the HP PC used to be a Windows 7 64 bt PC.)

So how do I make sure it gets when I install?

Thanks!!

---

### Post by hacksonfive on 2014-05-30
How much of the "try it" part of it works for you on your system? Are you able to do things like surf the web, install things, mount disks, or whatever else you may do with your computer? I ask because it seems so strange that the live environment would work just fine, but the installer fails.

My first suggestion, which kind of seems like a stab in the dark, would be to re-burn the iso, or download another iso and burn that to see if that's what's causing the problem.

---

### Post by Deaf Smith on 2014-05-30
Yes I surfed the web, but I didn't install anything.

Yes I just got a fresh package of Memorex  DVD+R 4.7 GB disk and am about to reburn using K3b.

Question.. for a HP ex-windoews PC is the ubuntu-14.04-desktop-amd64.iso the correct one to use?

Thanks.

---

### Post by mörgæs on 2014-05-30
Before burning more disks:

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Can be run from a live boot.

---

### Post by Deaf Smith on 2014-05-30
Ok I have the lshw.txt file. Is the CODE tags part of K3b?

---

### Post by mörgæs on 2014-05-30
Code tags are available in the advanced editor here in Ubuntuforums. Useful when posting terminal commands and results.

---

### Post by Deaf Smith on 2014-05-30
Ok, I guess this is part of 'Manage Attachments' (or else they have not enabled me to use CODE tags.)

But, do you want the .txt flle from this PC I am useing (_it's not_ the one I want to make the system for) OR boot up the PC I am trying to install the OS and do the 
'lshw' on that PC?

See I have two PCs (well actually 3 but that's another story.) 

The one I am on now I have Apache server, PHP, MYSQL, Java, C++, ... even COBOL (Open Cobol) and was made for alternate OS.

The other PC (HP Palivion that did have windows 7) is the one I am having problems with installing Ubuntu.

Thanks.

---

### Post by mörgæs on 2014-05-30
Please don't attach files. Did you open the advanced editor?

Lshw from the computer which gives problems.

---

### Post by Deaf Smith on 2014-05-30
ok. I got a live-booting distros from LinuxUser (Ubuntu 14.04 Beta) and it is running weird to. Won't even get to the live-boot.

Let me go get a DVD cleaning disk and see if that helps.

I'll let you know how that works out.

Thanks.

---

### Post by mörgæs on 2014-05-30
If you have an empty USB stick it's better to boot/install from that.

---

