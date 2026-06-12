---
title: "Compiling Question"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by DBrocks on 2008-06-13
Hey guys,

I tried using G4L to image my box to my FTP server. But, it didnt work. Apparently it can't work with my wireless card. However, i found a driver for it. is there anyway i can compile the driver (a '.gz') into the G4L cd, so it can detect my card? Thanks!

---

### Post by KingTermite on 2008-06-13
First, if you don't develop, you need the compiler tools installed. Get them by:
**sudo apt-get install build-essential**

Then, gz is a zip file (Gnu zip). You can unzip by typing (from terminal):
**gunzip file.gz** (might want to do it in its own directory in case it creates a lot of files).

Once its unzipped, it will hopefully be a source directory, or have a subdirectory called "source" or perhaps "src". In that directory, there will hopefully be a file called "makefile". Type **make **at the command line.

This will compile the source code (if no errors).

That's as far as I can take you..not sure how to merge them in.

---

### Post by Hospadar on 2008-06-13
What sort of wireless card do you have, and what driver are you using for it? could you provide a link to the driver?  Does a regular ubuntu livecd work with your wireless card fine?  If so you could probably use gparted to do this in combination with something like ftpfs or sshfs.

Also, as for compiling on the G4L cd, you'd have to boot up the cd, get build tools installed, download the driver (probably with wget) then build and modprobe/insmod the driver.  Probably you can get more specific help when we know the specific driver.

---

