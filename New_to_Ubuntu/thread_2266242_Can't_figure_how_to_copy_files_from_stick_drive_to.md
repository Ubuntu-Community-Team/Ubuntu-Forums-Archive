---
title: "Can't figure how to copy files from stick drive to hard drive in Clonezilla &amp; FreeDOS"
date: 2015-02-21
forum: New to Ubuntu
---

### Post by swampwiz on 2015-02-21
Here's my situation:

I just bought an HP Pavilion notebook, and not wanting Windows 8.1, I  decided to install Windows 7.  I used Tuxboot to make a bootable USB  stick drive to run GParted, which allowed me to repartition to the hard  drive in NTFS, from which I was able to install my old copy of Windows 7  Home Premium from another USB stick drive.  I fully understand that I  need to load in a bunch of drivers, and I downloaded them and put them  on yet another USB stick drive.  The key here is that the BIOS properly  recognizes when a bootable stick drive is attached.
 
So I am all ready to run the driver EXE files, but I need to somehow get  those files onto the hard drive.  However, in Windows, the USB stick  drive is not recognized!  And of course, the wireless modem is not  recognized as well, so I am stuck as there is no way to get those driver  EXE files onto the hard drive!  I tried using Tuxboot to run FreeDOS  & Clonezilla, but I couldn't seem to get the job done (in FreeDOS,  there only seemed to be the A: & C: drives, corresponding to the OS  & stick drive, without there being a drive corresponding to the hard  drive.) ](*,)
 
I have entered this same question to the HP Support forum, but since I  repartitioned the hard drive, they will probably tell me too bad, we  will only support you with our buggy and INCREDIBLY CRAPPIFIED install  of Windows 8.1.  Of course, if anyone can give me pointers applicable to  the HP system, that would be great - but I am looking here for advice  on how to use FreeDOS or Clonezilla or whatever else to just get me to  the point at which I can get the darned files from the USB stick drive  onto the hard drive, after which I presume that those driver EXE files  will do the trick.

Thanks!

---

### Post by nerdtron on 2015-02-21
>  I used Tuxboot to make a bootable USB  stick drive to run GParted,  which allowed me to repartition to the hard  drive in NTFS, from which I  was able to install my old copy of Windows 7  Home Premium from another  USB stick drive.

In windows, you can use the Windows 7 DVD tool from the microsoft website to create a bootable window 7 USB. This will make a USB format to NTFS automatically and create a bootable media for windows 7 installation.

> So I am all ready to run the driver EXE files, but I need to somehow get   those files onto the hard drive.  However, in Windows, the USB stick   drive is not recognized!  And of course, the wireless modem is not   recognized as well, so I am stuck as there is no way to get those driver   EXE files onto the hard drive! 

Your USB drive is probably not formatted for windows filesystem like FAT32 or NTFS.
I suggest you do the recommended install of Windows 7 using the windows 7 DVD tool. If you have free space on the USB drive, you can also put your drivers on that USB.


I don't even know Tuxboot and certainly i haven't had the need to use freeDos or Clonezilla just to install a windows OS. You don't need linux tools to install windows.


EDIT: as for the drivers, you can always download those from the internet, right? If you can't connect to internet, do you have a recovery or driver CD? or perhaps another computer in the house with internet connection?

---

### Post by swampwiz on 2015-02-21
OK, I dug around a bit and set up ubuntu 14.04 LTS on a USB stick drive, and have been able to get that boot up from Stick #1.  However, I have on Stick #2 - formatted in FAT32 - the files I want to copy over to the hard drive.  The devices that show up in ubuntu are:

- main (the hard drive for the system)

- casper (which when tried to access says unable to access)

- Computer (which has a bunch of folders and a few files, but this is not Stick #2!)

I suppose I will try your suggestion, but if I could simply get Stick #2 to show up, my problems would be solved.

---

### Post by nerdtron on 2015-02-21
Well then, you can provide us with more detail on Stick#2.

If it is fat32, you should be able to access it.
Post the output of the following commands while you are booted on Ubuntu:
```

lsblk
sudo fdisk -l
sudo parted -l

```

An a screenshot of your file manager where you see your drives and the error you are getting when you try to access it.

---

### Post by swampwiz on 2015-02-25
OK, I ended up making a USB stick drive that boots to Ubuntu Desktop, and then did the commands:

sudo mkdir /media/dirname
 
sudo mount -t vfat /dev/sdb1 /media/dirname -o uid=1000,gid=1000,utf8,dmask=027,fmask=137

This allowed the USB drive to be recognized, as I was able to copy the files.

---

