---
title: "google sketch up and google earth"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by naki on 2008-10-10
/How can I download sketch up for linux?
/ 
how can i download google earth for linux?

---

### Post by mkokotovich on 2008-10-10
Google "google earth linux"  That will take you to the official page where you can download the latest version. Else, sudo apt-get install google-earth should do the trick.  This method would be much easier.

Sketchup does not have an official Linux version.  If you are interested, you can install it with Wine, but that would most likely not be a walk in the park.

---

### Post by naki on 2008-10-16
I tried it in the terminal, but no sucess. What steps should I take? If have you specific instructions, I would greatly appreciate it!

---

### Post by mkokotovich on 2008-10-16
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) has very clear instructions, you should be able to follow them.  The instructions I gave for the terminal depended upon having a specific repository installed, which I forgot about.  This method will be easier.

---

### Post by dankegel on 2008-11-23
Sketchup is working fine for me, and probably will for anyone with a good nvidia card.  There are two or three hoops to jump through; see
  [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)
for a list of tips.  Also please report any problems you run
into there.

---

### Post by tom480 on 2008-11-23
I'm also a Ubuntu newbie trying to install Google Earth, using the amd64 version of Ubuntu 8.10.

I took mkokotovich's sugestion and followed the instructions at [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth), and got the following results:

[sudo] password for tom: 
sudo: ./GoogleEarthlinux.bin: command not found
tom@tom-desktop:~/Desktop$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
tom@tom-desktop:~/Desktop$ 

could one of you interpret this failure for me?

Thanks!

---

### Post by xravexheavenx on 2008-11-23
The version you have downoladed is for 32 bit...  Not 64

---

### Post by Moop on 2008-11-23
Enable the medibuntu repository and you can get google earth from there. 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by oldos2er on 2008-11-23
> **tom480 said:**
> I'm also a Ubuntu newbie trying to install Google Earth, using the amd64 version of Ubuntu 8.10.

I took mkokotovich's sugestion and followed the instructions at [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth), and got the following results:

[sudo] password for tom: 
sudo: ./GoogleEarthlinux.bin: command not found
tom@tom-desktop:~/Desktop$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
tom@tom-desktop:~/Desktop$ 

could one of you interpret this failure for me?

Thanks!

 Not sure, but you may have a corrupted download, so try downloading it again. FWIW I've downloaded and installed GoogleEarthLinux.bin on 64-bit Ubuntu 8.10, and it works fine.

---

### Post by diablo75 on 2008-11-23
See my signature.  ;)

---

### Post by etlpkby on 2008-12-22
I'm getting exactly same error too.

**This was working and now it isn't**. Maybe recent patches have bombed it? There's no 64bit version AFAIK, it's just 1 self-extracting linux archive

BTW: I'm running 8.10 and '2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux'

---

