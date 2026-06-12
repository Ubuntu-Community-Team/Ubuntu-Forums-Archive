---
title: "help with getting some files from HD"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by 1onething on 2008-07-20
last night i was looking at some stuff i probably shouldnt have been looking at:oops:
when i closed ie i noticed more than half of my desktop icons were gone (this was in XP)
and than most of the start menu was dissapearing as well, and apparantly task manager was disabled
i run a scan with spy sweeper and nod32
i was looking through some folders and decided to delete one that i didnt need anymore, it was about 2-3gb (this was a useless one with pics & stuff i had in it)
later i forgot i deleted that and thought that a folder abd i thought that the virus deleted 2-3gb of data, so i decided to just turn off the computer, and on my other computer i burned a disk of Ubuntu and im currently running Ubuntu from the CD, on the infected computer

I tried Windows safe mode and it wouldnt work, i also tried the windows CD as well, but it seems to take forever to get started
Ive done a windows repair from the cd before i dont think its ever took as long as it has today

anyways im hoping i could get to the hard drive thats has some of files (i have an external i can transfer them to)

both of my hard drives dont work one is my internal 320gb, and the other is an external 80gb
it says something about not being able to mount them and in the error paragraph it says something about it being marked with NTSF
I can write down the whole error paragraph if you want

im just trying to get some stuff off the HD WITHOUT deleting anything, than when im done  wouldnt mind reformatting the 'infected' 320gb HD
320gb is sata, 80gb is usb

Thanks for any help ](*,)

---

### Post by f37u5g0d on 2008-07-20
You're going to have to write down the entire error message before anyway can really help you.  I can tell you however that it should be possible to recover your lost data with a live CD so don't worry.  As long as the particular data you're attempting to get isn't corrupted.  I have done this couple times on friends computers.

---

### Post by 1onething on 2008-07-20
320gb SATA Drive
[http://i49.photobucket.com/albums/f265/houston9388/Screenshot.png](http://i49.photobucket.com/albums/f265/houston9388/Screenshot.png)

80gb USB Drive
[http://i49.photobucket.com/albums/f265/houston9388/Screenshot-1.png](http://i49.photobucket.com/albums/f265/houston9388/Screenshot-1.png)

is it to risky to force a mount?

---

### Post by dhughes on 2008-07-20
> **1onething said:**
> 320gb SATA Drive
[http://i49.photobucket.com/albums/f265/houston9388/Screenshot.png](http://i49.photobucket.com/albums/f265/houston9388/Screenshot.png)

80gb USB Drive
[http://i49.photobucket.com/albums/f265/houston9388/Screenshot-1.png](http://i49.photobucket.com/albums/f265/houston9388/Screenshot-1.png)

is it to risky to force a mount?

 Those screenshots are what you see when trying to mount a Windows hard drive while using an Ubuntu LiveCD?

**EDIT:**

 All I would do if in the same situation is use a LiveCD, make a spot to mount it to such as **/dev/windows** and then **mount -t ntfs /dev/sda1 /mnt/windows** although I'm sure people will correct me if I'm wrong since you may need to add some additional information or switches after "**mount -t ntfs**" part. Then stick a USB key in a slot, find it, usually under /media  do a lsusb to see where it is, mount that and send files to it.

 But I think that's pretty much what you're trying now, if I understand you correctly.

---

### Post by 1onething on 2008-07-21
> **dhughes said:**
> Those screenshots are what you see when trying to mount a Windows hard drive while using an Ubuntu LiveCD?

**EDIT:**

 All I would do if in the same situation is use a LiveCD, make a spot to mount it to such as **/dev/windows** and then **mount -t ntfs /dev/sda1 /mnt/windows** although I'm sure people will correct me if I'm wrong since you may need to add some additional information or switches after "**mount -t ntfs**" part. Then stick a USB key in a slot, find it, usually under /media  do a lsusb to see where it is, mount that and send files to it.

 But I think that's pretty much what you're trying now, if I understand you correctly.


actually im just going into 'Computer' and double clicking on the drives

---

### Post by Rolcol on 2008-07-21
When windows doesn't shutdown correctly it locks up the hard drive.  You have to forcibly Mount it with the command it tells you in that error.  Open up the terminal (Applications > Terminal) and enter this command: **sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force**.  I don't know the effect on your windows computer after running that.  To avoid this in the future, it may be best to install a safer internet browser such as [FireFox](http://getfirefox.com).

---

### Post by 1onething on 2008-07-21
> **Rolcol said:**
> When windows doesn't shutdown correctly it locks up the hard drive.  You have to forceably Mount it with the command it tells you in that error: **sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force**.  I don't know the effect on your windows computer after running that.  To avoid this in the future, it may be best to install a safer internet browser such as FireFox.

hey, that worked

Thanks =D>

one more question, since i tried reinstalling from the windows cd and it didnt work, should i just install Ubuntu and make it take the whole drive that way it clears everything, than i can install windows over everything and install ubuntu on a partion on the disk?

---

### Post by raydeen on 2008-07-21
Edit: Just saw your response and saw that the Windows re-install didn't work. The only other thing I can think of is try a Knoppix or DSL distro and see if you can access the HD and get your data off to an external drive. They both should come with NTFS support built in. If not, spend $30 bucks, get an HD enclosure and plug your drive into that and get your data off that way.

***

I had this happen to a friend of mine last week. I booted up his comp with his Windows CD and re-installed Windows to a new directory (windows.001) and then transferred all his files over and did a quick virus scan to get rid of anything that may have survived. Did all the updates and such and then installed Ubuntu with Wubi and told him if he must surf dirty, do it in Ubuntu. And if something does happen to Windows, he'll still have Ubuntu to fall back on so he can check his email and surf and such.

---

### Post by Rolcol on 2008-07-21
> **1onething said:**
> hey, that worked

Thanks =D>

one more question, since i tried reinstalling from the windows cd and it didnt work, should i just install Ubuntu and make it take the whole drive that way it clears everything, than i can install windows over everything and install ubuntu on a partion on the disk?
If you're going to install Windows over the Ubuntu install, why not just reformat the Windows harddrive using gparted that's included in the LiveCD?  System > Administration > Partition Editor

---

### Post by 1onething on 2008-07-21
this wont work for the external hard drive

is there a Windows Virus fix for use in Ubuntu Live Session?

---

### Post by PmDematagoda on 2008-07-21
> **1onething said:**
> this wont work for the external hard drive

Why not? Isn't the USB drive detected by Gparted?

---

