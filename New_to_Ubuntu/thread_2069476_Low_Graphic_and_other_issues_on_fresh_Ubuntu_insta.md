---
title: "Low Graphic and other issues on fresh Ubuntu install"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by myxoh on 2012-10-10
Solved!

EDIT: I managed to solve it myself... First of all I searched for the command to see my disk space... I discovered my drive was full, so after an LS I realise the "Documents" folder... I cd there and some of the things from windows that Ubuntu was trying to import were there... So I deleted the whole folder and rebooted. That fixed my issue! (including the low graphics issue)

I did a new install (my first Linux install, and my first Ubuntu install of course) on my HP Pavilion 7 (550 GB HD, AMD Radeon 6750M and AMD Radeon 6255G, 64 bits AMD A8 processor, Ubuntu x64 release):
The steps I followed for the installation were:<br>
1- Delete the HP primary partition for HP_TOOLS (200MB)<br>
2- Shrink my main partition (leaving 20 free GB more or less)<br>
3- Run installation from Ubuntu's CD by booting from CD (not from windows).<br>
4- Choose first default option (install Windows besides Linux).<br>

The bootloader prompted correctly, so I decided to check firstly if my Windows partitions was still working... tested it and rebooted, then logged into my Ubuntu partition.<br>
The error "your system is running in low-graphics mode" appeared, I try to have it resolved automatically with no success, and then tried to use the session anyway... in both cases the screen stayed black (or dark purple... I don't recall) so I rebooted.
On my third run I entered the command prompt in an atempt to try some of the fixes I've seen around.

1st thing I tried) : 

> sudo apt-get install fglrx

Which resulted in the download of the file...but when it was expanding the package the error "failed to extend .....(in each file)...no space left in device" appeared...then an error, and after the reboot Nothing.

2nd thing I tried) :

> sudo apt-get install --reinstall ubuntu-desktop

Same issue.. but after using this I realised now my system didn't even show me the "running in low graphics mode", it just took me to a dark purple screen and stayed there (I could still log in any terminal). Notice this MAY HAVE happened after throwing the first command, and maybe I didn't notice, because I tried one solution after the other.



Any tips? <br>
Please try to be as clear as possible as I'm not familiar with Linux environment... I do now one or other command, but please act as if I didn't know any, as I don't know many.

---

### Post by critin on 2012-10-10
Boot from live cd/flash and this time choose TRY-- LIVE.  It won't install, it will run from the cd.  Open gparted and try to get a screenshot of the disk to post.

---

