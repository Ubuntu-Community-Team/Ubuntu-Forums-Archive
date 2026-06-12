---
title: "Installation help on 12.10"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by Hunter84 on 2012-10-25
OK im looking to install just ubuntu on an old desktop i have and i wiped the hard drive. Although i dont know if ntfs is the right format but thats what it is. so i downloaded the version 'ubuntu-12.10-desktop-i386.iso' and opened it with winrar and put the files in it on a dvd. well i thought that was all i had to do. so the drive wiped and 'ready' pop in the disk and then it says boot disk failure? any ideas. did i burn the disk wrong? or not sure whats going on. any ideas? im new to linux but not windows.
:guitar:

---

### Post by will1982 on 2012-10-25
> **Hunter84 said:**
> OK im looking to install just ubuntu on an old desktop i have and i wiped the hard drive. Although i dont know if ntfs is the right format but thats what it is. so i downloaded the version 'ubuntu-12.10-desktop-i386.iso' and opened it with winrar and put the files in it on a dvd. well i thought that was all i had to do. so the drive wiped and 'ready' pop in the disk and then it says boot disk failure? any ideas. did i burn the disk wrong? or not sure whats going on. any ideas? im new to linux but not windows.
:guitar:

Try using the default windows burner.

Also, if you can, burn a 12.04 CD. I've heard of a lot of bugs in 12.10.

I *think* NTFS will work.

---

### Post by Hunter84 on 2012-10-25
Will try 12.04 and i forgot mention that i did use that burner. i will try it again though with 12.04. and thank you

---

### Post by squakie on 2012-10-25
You should be downloading the ISO and just use burn as image.  Copying the files to a CD will not work - you have to burn as an image.

---

### Post by ajgreeny on 2012-10-25
You also do not need to wipe the disk or do anything like that before you install.

Just choose to "use the whole disk" when you get to that point in the installation, and that is exactly what the installer will do; ie, delete anything on the disk and make the partitions needed automatically.

How old is the desktop machine?  You need at least 1GB ram and preferably more for 12.10 to work sensibly, and you also need a graphic card that can run unity 3D, as the 2D version is no longer available.  None of my computers will run 12.10 with unity, and they are not too old to still be very useful machines with the right OS (Xubuntu?)

---

### Post by Hunter84 on 2012-11-03
My desktop is perty old, its an hp pavilion a404, so should i get an older version of ubuntu that doesnt need 3d, i dont need that part. or even is there a way to get like 10.10 i had that one when it came out but lost the CD i burnt with it on it?

---

### Post by newb85 on 2012-11-03
In general, choosing an end-of-life (EOL) release because you have an old machine is a bad idea.  You're better off with a more current release of a lighter distribution.

10.10 hit EOL April of this year.
11.04 hit EOL last month.
11.10 and 10.04 LTS will hit EOL April of next year.
12.04 LTS will be supported until April 2017 (unless you go with Lubuntu).
12.10 will be supported until April 2014.

Xubuntu and Lubuntu are both great official alternatives for older/weaker machines.

The filesystem Ubuntu uses is EXT3.  You can't create it from Windows.  It will have to be set up during installation. (The installer should do it automatically.)

Squakie already said it, but I'm going to repeat it for good measure.  You should *not* extract the contents of the .iso file before burning it to the disk.  A disk burnt with the contents of the .iso is worthless for installation.  Follow the directions found at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

---

