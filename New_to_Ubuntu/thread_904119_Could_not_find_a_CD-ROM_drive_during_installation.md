---
title: "Could not find a CD-ROM drive during installation"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Alcove on 2008-08-28
Hello everyone. I am trying to install Kubuntu 8.04.1 with the alternate desktop CD (the normal one would not work). The CD boots fine, but after choosing the keyboard configuration, it says that "No common CD-ROM drive was detected." It won't install without it, so I'm stuck for now. I'm a newbie, so please bear with me. Any help would be greatly appreciated.

---

### Post by cdtech on 2008-08-29
Do you have a disk controller setting within your BIOS? You may need to set it to Enhanced mode.

---

### Post by Alcove on 2008-08-30
It looks like it's already on Enhanced, the other settings didn't work either. :(

---

### Post by cpradio on 2008-11-24
I had this issue too, I solved it by hitting ALT + F2, Enter to activate the console, and typed the following:
modprobe ide-scsi
modprobe ide_generic

Then I went back to the first terminal, ALT + F1, and had it detect the hardware again.

---

### Post by cpradio on 2008-11-25
Just an FYI, I discovered the above only worked with Hardy Heron.  I couldn't get it to work with Intrepid Ibex

---

### Post by tomtom1982 on 2008-11-25
Which kind of drive are you using?

I had the same problem with a LG DVD-RAM drive with LightScribe-Feature.

So I took an old DVD-ROM drive an put in on and everything works fine. 

I had have the problem with Ubuntu and Sidux but Debian Etch/Lenny Beta works fine.

---

### Post by roshanjose on 2008-11-25
first check whether your bios is detetcing....

if your bios isn't detecting then the cd isn't connected properly

if you Bios detects.....

then run this command in terminal:

mount /mnt/cdrom

---

### Post by Alcove on 2008-11-26
I don't know what type of cd drive it is, though I put a different one in and it worked fine. Apparently Ubuntu doesn't support as much hardware as it could....

---

