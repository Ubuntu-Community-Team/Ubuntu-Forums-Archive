---
title: "How to change name of Hard drive"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by barlrol on 2008-05-12
Hi im a noob obviously and I'm trying to change the name of my hard drives.  For example there is a hard drive that goes to my desktop when mounted that says 203.9 GB Media which is mounted in /media/applications but how do I change the actual name of the hard drive to Applications?

---

### Post by overdrank on 2008-05-12
> **barlrol said:**
> Hi im a noob obviously and I'm trying to change the name of my hard drives.  For example there is a hard drive that goes to my desktop when mounted that says 203.9 GB Media which is mounted in /media/applications but how do I change the actual name of the hard drive to Applications?

Hi and welcome, you may find some help here
[http://ubuntuforums.org/showthread.php?t=513168](http://ubuntuforums.org/showthread.php?t=513168)

---

### Post by barlrol on 2008-05-12
Sorry this thread didnt really help me...I changed the stupid mount point to Media Applications and i told fstab to put dev/sda1 or whatever in that and its volume name is still 203.9 GB vs Applications

---

### Post by Pijits_1 on 2008-05-12
Can't you just go to the Places --> Computer folder, right click on the drive and just change the name to whatever you need. I did that for my 250G HD and it shows up as that name even under windows.

---

### Post by barlrol on 2008-05-12
This was my first thought...I try and do this in 8.04 and it says "The item could not be renamed""Sorry couldnt rename 203.9 GB Media to Applications...Operation not supported by backend

---

### Post by robertsaron on 2008-05-13
I am having a similar issue. In 8.04 of Gnome when attempting to rename a drive this is the error that pops up:



The item could not be renamed:
Sorry couldn't rename "movies" to "movies1";
Error renaming file: device or resource is busy.

I have tried to force it by doing:

sudo mv movies movies1 --force but then get the same or different error. When doing sudo nautilus to change permissions, the permissions do not stick. I have multiple drives, and am experimenting. The movies drive is a linux formatted ext3.


EDIT:

NM, i found the solution while forum hunting:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by ahso4271 on 2010-05-29
still the same on 10.04. How do i change from somethin alike 52GB HD to myApplications or whatever.

---

### Post by John Bean on 2010-05-29
Give the disk a label. There are many ways to do this but I usually use Gparted: right-click on the ***unmounted*** disk/partition you want to label and select "Label" from the context menu. Type in the label text and apply the changes.

By default the system will use the disk label (if it has one) as a name for the mount.

---

