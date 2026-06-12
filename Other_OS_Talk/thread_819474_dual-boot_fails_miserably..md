---
title: "dual-boot fails miserably."
date: 2008-06-05
forum: Other OS Talk
---

### Post by MaxIBoy on 2008-06-05
Everything was basically normal before. When I installed Ubuntu 8.04 on my hard drive, I kept a 45 gig partition for XP, which I never used. I decided to give CrunchBang Linux a try, using that extra partition. That's where things went wrong... in a manner of speaking.


I booted from the CD and ran the installer. Now, this is what the bootloader menu looks like:

ubuntu linux 2.6.something
ubuntu linux 2.6.something (generic)
ubuntu linux 2.6.something (recovery mode)
ubuntu linux 2.6.something
ubuntu linux 2.6.something (generic)
ubuntu linux 2.6.something (recovery mode)
ubuntu linux 2.6.something
ubuntu linux 2.6.something (generic)
ubuntu linux 2.6.something (recovery mode)
memtest86+

I think that's what it looks like. This is from memory.



All of them lead to my main Ubuntu installation. However, when I  mount the 45-gig partition I see the installation files of the CrunchBang installation. 



I suspect that the problem originates from me unchecking "install boatloader" during the installation of CrunchBang. I reasoned that GRUB was already installed so I didn't need to install it. 


How do I fix this? Ubuntu still works just fine, it's just irritating to have three different bootloader options for it and none for CrunchBang, which I really want to try out in a non-liveCD environment.

---

### Post by cardinals_fan on 2008-06-05
Edit your /boot/grub/menu.lst on the Ubuntu partition and add CrunchBang.

---

### Post by MaxIBoy on 2008-06-05
All right, thanks. A friend of mine actually helped me edit the file to get the extra Ubuntu listings off (he said they were older kernals.) Don't worry, I backed up the file. :)

Now I just have to figure out how to add CrunchBang. Don't worry guys, I'll just google it.

EDIT:
After some tweaking of the file, and a lot of Error 11: unrecognized device string, I just decided to reinstall CrunchBang and let the installer reinstall GRUB (wow, that's a mouthful.) Worked perfectly, and I'm impressed with CrunchBang. Runs very, very fast, starts up very, very fast. It installs extremely fast, about eight minutes instead of 15 (my previous record while installing Ubuntu.)

---

