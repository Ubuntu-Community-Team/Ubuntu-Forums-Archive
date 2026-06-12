---
title: "I think I accidentally Overclocked my GPU"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by twostepsfromhell on 2013-04-30
I have a Samsung NP500 laptop with Nvidia GT650M Optimus. I have installed bumblebee on my 13.04 and it works fine. Yesterday I was curious at measuring the GPU temp and found somewhere that i install NVCLOCK and use the command nvclock -t. I did that and installed nvclock and nvclock_gtk. The command however did not work for me and it didnt show the temps. But now my system is overheating and fan is running. bumblebee says that the dedicated graphics card is off. Still the heat level is high. I uninstalled Nvclock promptly, but the heating remains. [NVClock]("http://www.linuxhardware.org/nvclock/") is a utility to primarily overclock the GPU. It is an old software with last release in 2008. Did I overclock my GPU accidentally by installing it ? If so how can i measure the clock speed ? How can i reset it to stock speeds ?

---

### Post by ppjdee on 2013-04-30
My knowlege is very limited in this, but no, it should not have OC your GPU just by installing it (I could be wrong). And have you tried the purge command when uninstalling it? 
I'd imagen it would un-do any OC it could have done just by uninstalling it.
Sorry, sure this is pretty useless info. :D

---

### Post by twostepsfromhell on 2013-04-30
Thanks for the quick reply ppjdee. Can you tell me how to use the purge command ?? Is the Overclocking done on a driver level or a firmware level ?? I mean if it is done in the firmware level even when i boot into windows it should be overclocked rite ?? even with the software uninstalled. Do you have any info on that ?

---

### Post by r.stiltskin on 2013-04-30
The command is

sudo apt-get remove --purge nvclock

but I doubt it will make any difference.  Purge deletes the package file (.deb) from your apt archive (/var/cache/apt/) and also deletes the program's configuration files (if there are any) from your /etc directory, but neither of those things should make any difference in how your system runs after uninstalling the program.

Does the laptop run correctly in Windows?  If it does, at least you know that you haven't messed up the Nvidia card itself.

---

