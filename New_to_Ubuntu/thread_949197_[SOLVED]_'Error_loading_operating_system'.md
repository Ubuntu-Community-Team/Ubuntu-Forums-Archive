---
title: "[SOLVED] 'Error loading operating system'"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by sheri68 on 2008-10-15
Hello I am new2 to the ubuntu thing. I have recently tried to redo my server and after installing ubuntu 7.0.4 I have gotten the black screen with 'Error loading operating system' on the screen after restarting can anyone help me with this problem? I ahve looked at many places for this problem however I can't find anything to help me with it.
Thanks to the gods who answer this post!!!!!:confused:

---

### Post by ryanhaigh on 2008-10-15
I think you will find that the error your recieving is from your bios. I get the same or similar error message sometimes when I don't have a hard drive in the machine however I would guess that your issue is more likely to be the boot order in your bios, perhaps you made the cdrom the first boot device and your hard drive is not there or you have selected the wrong hard drive?

---

### Post by Keen101 on 2008-10-16
Yeah you should normally get a grub error if Grub is messed up. however it sounds like your BIOS cannot find any hard drive at all!

---

### Post by sheri68 on 2008-10-16
thanks I changed the boot order and it seems to have worked however, is it normal on the first boot to get a whole listing of the files that I am guessing are installed?  kinda looks a little like command line stuff.

---

### Post by sheri68 on 2008-10-16
ok now I am getting a root file system in read only mode.  I have a single drive connected so there are no other drives for a grub error.

---

### Post by cariboo on 2008-10-16
You have been dropped to a root prompt because there are corrupted files on your hard drive from improper shut down.

You said you installed the server version, I hope you realize that there is no gui included in the server version. It is command line only. You can install a gui, but I would suggest getting some experience using the LiveCD before installing the server version. Maybe install the desktop version first and add the server components later.

Jim

---

### Post by Keen101 on 2008-10-16
> ok now I am getting a root file system in read only mode. I have a single drive connected so there are no other drives for a grub error.

yeah the srever version is command line-only. running > apt-get install ubuntu-desktop might install gnome, but if you really want a gui ubuntu it might be best to just use the live-cd (or alternate install disk) to install a normal version, and then just tweak it for running a server.

---

### Post by sheri68 on 2008-10-16
thank you to all of you!!

---

