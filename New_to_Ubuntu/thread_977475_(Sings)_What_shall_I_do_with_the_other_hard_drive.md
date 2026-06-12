---
title: "(Sings) What shall I do with the other hard drive?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by sqrooup on 2008-11-10
I have a second hard drive (250GB) sitting in my PC, with the remains of a corrupted version of Gutsy Gibbon, less than 11 months old. It became corrupted when downloading drivers for my video card.

Ideally I would like to put Kubuntu on to it (have an 8.04 disc) or even Edubuntu, just to try it out (again, have an 8.04 disc).

How can I; 
Test the drive to make sure its OK?
Reformat the drive?
Install the selected version without it wiping my first hard drive (400GB)?
Have a menu to select the version I want to use?

---

### Post by superprash2003 on 2008-11-10
you could connect your 250gb drive to your PC as slave.. then boot to the 400gb ubuntu and format the 250gb drive ( system->administration->partition editor).. if you dont see partition editor , install gparted by typing sudo apt-get install gparted    in the terminal..once done, boot live cd and install your linux OS to the 250gb hdd, grub would recognize it and create bootlist accordingly..

---

