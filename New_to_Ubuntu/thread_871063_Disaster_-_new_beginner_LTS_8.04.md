---
title: "Disaster - new beginner LTS 8.04"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Geoff.Lezemore@TalkTalk.n on 2008-07-26
Oh dear,
I loaded the LTS CD as I understood from the wrapper I could install Ubuntu alongside Windows XP while I tried things out.  My observations follow:-
1. I was given an option in the Install process to take a guided partition set-up or .. or ... or Manual.  There was not description that "Manual" meant I would be able to set-up to run both OS.  So I selected the default guided option.
2. I saw Linux and quite liked what I saw.
3.  I attempted a reboot (repeatedly) and got GRUB Error 18.  After spending about an hour in the forums I see that I need to reset my BIOS hard drive settings except my BIOS does not offer the indicated option.  Or there is an option to create a dummy \root partition (I think), but I cannot find how to do this.
4.  So, I have no way forward, hence this expression of fury in this forum.
5.  I guess I am going to have to reformat my whole drive and reinstall XP / rebuild my installation.  It is only fortunate that I decided to try Linux on my laptop which is not critical to me right now.  So, my recommendations to Canonical or other people follow:-
6.  Recommendation # 1:- If Linux is to succeed with the great mass of Microsoft users, it must offer a trustworthy entry and this to me means there must be a "back out" option from the outset.  In other words the LTS Installation CD should carry an option at the highest level "Uninstall".  This should be robust and fool-proof.  This would have enabled me to proceed by at least getting back to where I started.  As it is, I can't.
7.  Recommendation # 2:- All instruction options on the install process should explain the function that is to be achieved.  A word such as "Manual" is for geeks.  It needs to say "To allow operation of dual OS" or other similar function statements, even if these are listed under a "Help" option.  Or guidance should be given to work through Manual Name XYZ pages NNN to MMM, so that there is no doubt on what the options mean.
8.  Sadly I am now going to have to reformat my hard drive and probably won't return to Linux for some years.
Sorry ...

---

### Post by appi2012 on 2008-07-26
It usually has more options including:
"Guided: Resize existing partition and install into the free space."

That works almost always. Also, uninstalling ubuntu is as simple as deleting the ubuntu partition, or installing Windows over it. However, does windows have  a uninstall option? The only reason everything works out of the box is because it comes preinstalled. Believe me, installing windows is a horrible experience. I recently reinstalled both windows and ubuntu. ubuntu took about 2 hours for me to get it working, whereas windows took at least 5. I had to download tons of drivers, antivirus etc. :)

If you still want to give linux a go, but don't want to spend time getting it to work, it comes preinstalled on some dell systems. :)

This tutorial is very very useful to begginers: 
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

If you ever want to try linux agian, without ordering a new computer, I would definately recommend that site.


Also, try asking around in these forums for answers to your questions. As for grub error 18, look here:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by SunnyRabbiera on 2008-07-26
please make sure to follow guides you may find on the internet, and just dont install a new OS without learning about it first.

---

### Post by Old_Grey_Wolf on 2008-07-26
Try this before you reinstall Windows.

You need to boot the computer with windows CD. Then go to recovery mode. Then run the command fixmbr.

This will re write your master boot record. Then you will be able to boot with Windows.

---

