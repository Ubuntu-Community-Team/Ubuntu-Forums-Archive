---
title: "Machine freeze (Xserver)"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by jakobh on 2008-05-27
Hi,

I have now tried to install  *buntu(Hardy Heron) from 5 different media - all md5sums hasbeen checked checked

Ubuntu install CD
UbuntuStudio Alternate DVD
Xubuntu install CD
Kubuntu (3.x) Install DVD
Kubuntu (4) both via Wubi and from 2 x from CD(currently installed)
Only the last is the AMD64 variant the others are i386

I have also downloaded other distros and the mandriva based installs, all debian based fail so far. but Kubuntu seems very much faster than PCLOS now to my woes :

Excepting Ubuntu studio (which ends in a black blank screen, and will be left out for the rest of the post) I seem to end in the same place or at least similar with a frozen (i'm guessing) Xserver.

Common for all is that they must be installed in safe graphics mode.

Xubuntu and Ubuntu freezes the machine pretty much the same :  when chosing timezone on the map, I tried Ubuntu 2 times first freeze when I was curious enough to click the release notes.

Both Kubuntus continue from here, and the installation finishes, and I boot up again and then the fun starts. 

Usually I make it to login, 
some times the freeze is in the middle of drawing the blue background. 

Often I even manage to login - with sound and everything so it seems normal, if I hurry I can start the updating process and sometimes even make it to start downloading. 

At other times I have tried to enter the K-menu and choose a program or something.

But it's always the same it stops after max than 40secs, and the only exit is the ever dreaded hard reboot - and as my reset button doesn't work it's a real hard hardreboot.


I have tried to 
           dpkg-reconfigure xorg-xserver 
with no luck - this might have been another inst, debian or some

So yesterday I got really in the mood and found a way to get a console at what I have learned is runlevel 3, this is not easy but I found this [http://ubuntuforums.org/showthread.php?t=249282](http://ubuntuforums.org/showthread.php?t=249282) and did it. (initial boot to recover) then when loggin in I found a thread (can't find again) telling me to 

SUDO -s -H after logging in as myself

Then I could update all I wanted so all security update and what have you was done, no change. So via aptitude I found the restricted Nvidia drivers and i believe I installed them but there is no change.

I will shortly here after try another "fix xorg" from the recovery boot and/or a dpkg-reconfigure xorg.xserver EDIT: only made it worse ends in the black screen now

If that does not work I'm lost, I have searched high and low and tried just about anything advised but to no avail, and much as I hate to I might just have to give up - hope someone can help(sorry about the lengthy post)

/Jakob

PS I'm running a Pentium D 925 (3.0ghz) 2GB RAM and a ASUS EN8600GT 256MB - 80GB disk with nothing else on it (Vista is on a seperate disk that I can unplug and feel safe when experimenting)

---

