---
title: "Ubuntu 8.04 update question"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Rodd_Roddy on 2008-05-26
Very new to Ubuntu 8.04 LTS deskstop edition .. slowly understanding Linux 
question
 
the other day there were some updates that i downloaded from the update manager.. now for some odd reason when i boot into Ubuntu it goes to this. Before i was able to get to the openin screen where type user name/ password.

busybox v1.1.3 (debian 1:1.1.3-5ubuntu12 Built-in shell (ash)

enter 'help' for a list of built-in commads
(inifrants)


at this point I usually juss restart computer select Ubuntu .. esc button and one of the options of recovery Ubuntu

one other point i have it set up for dual boot with Window XP

thanks in advance for the help !!!

---

### Post by rraj.be on 2008-05-31
Generaly if you are getting into the screen as you said  "initramfs bussy box" shell means there is some what problem with your kernal itself.

just the problem might be something like missing index of files or innode etc.

and  you have mentioned that you have  dual boot with xp and now could you see your GRUB menu when you are turning your pc ON.

then the next clarification that i need is whether you have turned off your pc without properly shutting down the OS.

this shud be the main cause for this kind of problem generaly.

just tell the details..that you have done  before this problem

---

### Post by wild_oscar on 2008-06-28
> **rraj.be said:**
> Generaly if you are getting into the screen as you said  "initramfs bussy box" shell means there is some what problem with your kernal itself.

just the problem might be something like missing index of files or innode etc.

and  you have mentioned that you have  dual boot with xp and now could you see your GRUB menu when you are turning your pc ON.

then the next clarification that i need is whether you have turned off your pc without properly shutting down the OS.

this shud be the main cause for this kind of problem generaly.

just tell the details..that you have done  before this problem


I actually have a similar problem. A few days ago it booted in the busybox. I rebooted and that screen never appeared again. However, the kernel seems to have broken something, as the desktop is unresponsive the first time a user logs in. The issue is described here: [http://ubuntuforums.org/showthread.php?t=814079&page=2&highlight=login+desktop+icons]("http://ubuntuforums.org/showthread.php?t=814079&page=2&highlight=login+desktop+icons")

---

