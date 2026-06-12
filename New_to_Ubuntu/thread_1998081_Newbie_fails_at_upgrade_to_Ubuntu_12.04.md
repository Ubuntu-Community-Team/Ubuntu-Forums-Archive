---
title: "Newbie fails at upgrade to Ubuntu 12.04"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by gyre2 on 2012-06-06
I'm keen to learn Linux but I am totally stuck.

I had "Oneiric Ocelot" installed and running well on my old spare laptop for about 9 months.  But ever since updating to version 12.04, Ubuntu has not worked.

What I always get is one or both of the following: 
1) Partial version of the GUI: no launcher on the left-hand side of the screen, unable to close windows, no update manager, no Software Centre, no Firefox (or other software), can't connect to internet, etc.  After a minute I get an error saying that "Compiz cannot launch".  I'm out of my depth on that.  Accessed Compiz through restore mode but I'm afraid to tinker with it without guidance.
2) Black screen with a cursor (arrow) in the middle.   No command prompt, and F7 and alt-ctrl-T do nothing.

My first update attempt was via the update manager within "Oneiric  Ocelot".  When that update failed, I created a USB live key and  re-installed Ubuntu 12.04 from that twice, but with the same results.  

Interestingly, if I select the "try before installing" option when I boot up from the USB live key, the new version of Ubuntu seems to work fine.  It only fails when I actually install it.

Sometimes I can get to a command prompt by pressing F7, and wish I knew how to fix it from there.  I have a basic familiarity with command prompt and want to learn more, but using it to fix the operation system sounds like a big job. 

Any advice?  The volume of support info out there is overwhelming, but feel free to refer me to some relevant background reading as "homework", as I am trying to learn Linux thoroughly as I go along.  For my Linux experiments I'm using an HP Pavilion 2500 laptop.  

Thanks kindly!

---

### Post by z3nhakr on 2012-06-06
do you have compiz settings installed? if so it might have compatibility issues with unity but i haven't ventured there since i moved to unity. 
in the 12.04 install there is an option to update the installer. it is on the first step. can you get to this?

---

### Post by gyre2 on 2012-06-06
Yes, I checked that "install updates" box on the installer and the computer was connected to the internet throughout the install.

---

### Post by Hadaka on 2012-06-06
Since you are trying to upgrade from 11.10 to 12.4 i would suggest first
backing up everything in 11.10 . Then.. wipe the drive and go for a fresh
install of 12.4   Upgrading seems to work for some users but not all. This way
if 12.4 just wont load on your machine,you can always reload 11.10 from your
backup.  you could also do a dual boot install and choose between 11.10 and
12.4.

---

### Post by gyre2 on 2012-06-06
Thanks.  

I think 11.10 is completely gone from my computer.  When it boots up there seems to be no option to boot in 11.10.

I'll try re-installing 11.10.  Bear with me on a couple of basic questions:

- When you say wipe the drive, I assume this means that at the time of running the 11.10 installer I simply select "overwrite 12.04 with 11.10" (or whatever) -- or do I have to do some separate procedure to wipe/format my hard drive before I run the 11.10 installer?

- So is 11.10 still supported?  I thought one of the main points of Linux is that only the latest version is supported (for five years in the case of 12.04).

Greatly appreciate the help... it's all still pretty hazy for me.

---

### Post by gyre2 on 2012-06-12
After a lot of fooling around I've got something working:  Ubuntu 11.10.  This did not work at first: the trick was to plug the computer into a wired internet connection then download and install the "STA" drivers for the NVidia video card and the Broadcom network card.  Prior to that, 11.10 used to freeze unpredictably (and the wireless didn't work).

Also installed or tried installing the following, which froze either during the installation process and/or during boot-up: Ubuntu 12.04, 11.04, 10.04, and 10.10; Lubuntu 12.04, and Fedora 14.  I bet the wired-internet-download-and-install of STA drivers would have worked on any of those OS's that would get past the install and boot stages (but I didn't try).

Again I'm using an HP Pavilion 2500 laptop and I see a lot of people have had challenges getting started on these computers... I found a "compatibility" thread in a different forum so maybe I should post this there.

I'm just glad I can now get on with learning about file management and using the terminal and suchlike.  Much more fun!

---

