---
title: "Need help finding my hard drive"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by aj6 on 2013-09-11
Alright, so I couldn't figure out how to use an image backup for windows over my network because it didn't want to work so I am using ubuntu to copy the image to my hard drive but I don't know how to actually save it in the hard drive so that my backup disc can find it, can anyone help me out?

I have no idea how to even make my hdd appear under devices, I don't even see devices on my browers :\

/e

it tells me that sda1 is already mounted under media, as well:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   960094207   480046080   83  Linux
/dev/sda2       960096254   976771071     8337409    5  Extended
/dev/sda5       960096256   976771071     8337408   82  Linux swap / Solaris

---

### Post by cody1233 on 2013-09-11
Welcome to the forum!!

From this, it looks like you only have 2 partitions on your HDD, SDA1 (Your root filesystem), and SDA5 (Swap space).  The "Extended" partition contains only the Swap partition (it is generally used as a organizational tool).  So are you looking for another device entirely or are you looking for another partition?

---

### Post by aj6 on 2013-09-11
no no, i'm just trying to explore my hard drive. like on windows you can find your program files and stuff in the c: drive, so i thought maybe there is something like that on ubuntu so i can attempt to copy the file i need to into that folder and try to recover with my backup image

---

### Post by cody1233 on 2013-09-11
Oh, OK...most of the programs that you install in Ubuntu will be in the /usr/sbin/ directory, but there are other directories that may have programs and other binary files in them.  Are you trying to restore a windows installation that you had?  Is that what the backup image is for?  You won't be able to copy files into this directory as it is owned by root.

---

### Post by aj6 on 2013-09-11
> **cody1233 said:**
> Oh, OK...most of the programs that you install in Ubuntu will be in the /usr/sbin/ directory, but there are other directories that may have programs and other binary files in them.  Are you trying to restore a windows installation that you had?  Is that what the backup image is for?  You won't be able to copy files into this directory as it is owned by root.

yes, that's what the image is for, to restore windows. so is there no way to do this? :(

---

### Post by cody1233 on 2013-09-11
What is the file extension of the recovery image?

---

### Post by aj6 on 2013-09-11
.vhd

I'm not really sure about how to make the recovery disc recognize the file, but I think it just has to be in the root :\

---

### Post by cody1233 on 2013-09-11
That is a image for a Virtual Hard Drive and I'm not sure if you can mount that at boot or if you have to have a Virtual Machine to use it.  Anybody else have any idea???

---

### Post by aj6 on 2013-09-11
> **cody1233 said:**
> That is a image for a Virtual Hard Drive and I'm not sure if you can mount that at boot or if you have to have a Virtual Machine to use it.  Anybody else have any idea???

i dunno i guess, i made it with windows' default backup image maker, so i imagine that the boot disc will recognize it, i guess my issue is trying to get it onto this hard drive. i don't have an enclosure or anything to try to transfer the data and i think my only option right now is to try and transfer it over the network from my laptop so yeah. thanks anyway

---

### Post by cody1233 on 2013-09-11
you might want to post something about your problem in the Virtualization section here...it might get more traffic.

---

### Post by Mark Phelps on 2013-09-12
Windows default backup/restore will "restore" that image to the same location as it was on the original drive, that is, if it was the first partition on the old drive, it will be the first partition on the new drive.  IF you have something else in that location on the new drive, it will get overwritten.

---

### Post by cmcanulty on 2013-09-12
i think first you have to boot to a live CD image and partition HD to ntfs or windows image won't see HD

---

### Post by Mephisto Pheles on 2013-09-13
You will need to create an NTFS partition for that windows image first. assuming that you will want to use Windows from that image. 
And you will need some linux program that can read that windows image in order to copy it to the NTFS partition.

I doubt that you can use an image like that for a virtualbox or anything. You'll need to install windows in a virtual image for that to work.

Correct me if I'm wrong

---

