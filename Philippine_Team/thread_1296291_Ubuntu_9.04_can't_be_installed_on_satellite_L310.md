---
title: "Ubuntu 9.04 can't be installed on satellite L310"
date: 2009-10-20
forum: Philippine Team
---

### Post by jaceleon on 2009-10-20
I need some help here, pare!

As I mentioned in the other post here, I have a friend that I totally converted into a Ubuntu lover. So She did something as part of her "spread the love" mania on Ubuntu.

She invited a friend all the way from Los Banos, just to have her Satellite L310 dual-boot with Ubuntu. It has Vista pre-installed there.

I divided her drive to 3. One for Vista, one for Ubuntu and one for the common files between Windows and Ubuntu (which I named "documents")
The problem is that whenever I try installing it (like putting it on separate partition than Vista) it says:

The partition cannot be formatted because the installer cannot unmount
/media/TOSHIBA/ SYSTEMVOLUMESYSTEM/ VOLUMEVOLUME

or something like that (I just remembered parts of the error. Somehow I memorized the directory. I'm sure of the directory.
And then it asks to go back or continue, but whatever I choose, mga pare, it goes back to the partition screen in the installation.

I tried using the liveCD's (on a USB< as I can't burn disc) terminal to unmount the said volume (using the umount command), but it says that

/media/TOSHIBA/ SYSTEMVOLUMESYSTEM/ VOLUMEVOLUME is not mounted

but still the error goes,and I can't install Ubuntu 9.04 at all.
Also the installer can't detect the remaining capacity left on the Windows Drive.

I need some help here, also I noticed that there is no "side-by-side" installation option in the installer.

---

### Post by Edgar Ilaga on 2009-10-21
Did you repartition/resize the disk using Vista's Disk Manager or using gparted or a similar tool on Ubuntu? There's an issue with resizing partitions pre-installed with Windows Vista using the disk manager provided with the Ubuntu CD. I encountered this once, and a quick trip to the Vista Disk Manager (resized the Vista partition, created a new data partition, and freed up the rest of the space w/o assigning it to a logical drive) fixed the issue.

---

### Post by jepong on 2009-10-22
I'm from LB... install it yung Wubi na lang... no need to repartition... etc...

---

### Post by jaceleon on 2009-10-23
Solved ko na po! I used Karmic Koala Live USB on installing! Works like a charm! Thanks na rin po!

---

