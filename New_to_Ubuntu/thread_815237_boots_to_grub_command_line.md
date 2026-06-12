---
title: "boots to grub command line"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by The Oz on 2008-06-01
I am having some trouble lately.  I installed Ubuntu 8.04 a while back, but now I am having troubles with grub.  When I select any entry in the list I get the grub command line.  I have tried reinstalling grub to my MBR and it did not help.

This is what happens step by step:
1. I start up the computer
2. Grub boot screen shows up and I select an OS
3. After selecting an OS it takes me to the grub command line that says:
"minimal bash-like line editing is supported" yada yada
grub>

I can type in commands but I am not sure how to boot ubuntu or XP from the command line.  Is there any way to make grub the way it was before?

---

### Post by spiderbatdad on 2008-06-01
Sounds like grub can't find the kernel. You may need to mount your file system from the live cd.
Then run fdisk -l make sure the partition is formatted correctly.

Or check Id from the prompt you get to see if your file system is mounted. Then maybe: grub> configfile (sda0)/boot/grub/menu.lst  

Long thread here, with some good info on the last few pages:[http://ubuntuforums.org/showthread.php?t=646570&page=4](http://ubuntuforums.org/showthread.php?t=646570&page=4)

---

### Post by Prospero2006 on 2008-06-01
Grub can bug out on you, but it's usually fixable if it's strictly a grub configuration problem. 

Two options:
1.) Boot a live cd and get to your /boot/grub/menu.lst file
      -Back it up, but try different settings.
2.) You can manually pass commands to grub when it asks
    you which OS you want. So, you could try hd(0,0) or hd(0,1)
    or hd(1,0) etc.... directly from the grub command line until it
    picks up what you are looking for. 

    -The hd(0,0) parameter may not be what you need to change, but
      all parameters are editable at that point.

---

### Post by The Oz on 2008-06-01
> Sounds like grub can't find the kernel. You may need to mount your file system from the live cd.
Then run fdisk -l make sure the partition is formatted correctly.
If I type fdisk -l into terminal on the live cd and I get nothing.
> Or check Id from the prompt you get to see if your file system is mounted. Then maybe: grub> configfile (sda0)/boot/grub/menu.lst
I am not sure what you mean.  I am quite new to linux.  As above i get nothing when I type fdisk -l

And now I do not get the option to select an OS, it just goes straight to the grub command line.

> Two options:
1.) Boot a live cd and get to your /boot/grub/menu.lst file
-Back it up, but try different settings.
2.) You can manually pass commands to grub when it asks
you which OS you want. So, you could try hd(0,0) or hd(0,1)
or hd(1,0) etc.... directly from the grub command line until it picks up what you are looking for. 
What settings should I try?  And as above I do not get the option to select an OS anymore.

---

### Post by spiderbatdad on 2008-06-01
sorry you will need sudo: as in sudo fdisk-l

To mount your file system from the live cd make note of the / partition # from the output of fdisk -l

Then run ```
sudo mkdir /media/sda
sudo mount -t /media/sda
```I believe that will do it, as ext3 should be auto detected.

Guess I'll try it now.

---

### Post by spiderbatdad on 2008-06-01
k. this is what I did:
Booted live cd. Ran ```
sudo fdisk -l
``` saw that /dev/sda1 was my linux partition.```
sudo mkdir /media/sda
sudo mount -t ext3 /dev/sda1 /media/sda
```
 Of course I had a desktop, so I could see the volume appear. But from the command line, you should now be able to:
```
cd /media/sda/boot/grub
ls -al
```There may be a backup of your original menu.lst. Just replace the current one with it, if you have. Otherwise you may be able to match the partitions to your fdisk -l

---

### Post by The Oz on 2008-06-01
Ok, I think I have found the problem.  In the menu.lst there is nothing.  it is just a blank file.  If I try to delete it, even with sudo and su it says file not found.  (yes I spelled it correctly)  rm, cp and mv does not work on this file as well.  Also I can not rename any of the backups to menu.lst.  What is the issue?

EDIT: In nautilus I can not see the menu.lst files, only in terminal. (I have show hidden file sand folders checked)

EDIT2:  If I try to copy a backup to another drive, rename it and move it back to /boot/grub I get this error: Error opening file '/media/hda/boot/grub/menu.lst': No such file or directory

---

### Post by spiderbatdad on 2008-06-01
Try startx to get into your GUI. Then run: ```
gksu nautilus
```
This will open your file browser with admin privileges. You'll be able to navigate and edit system files freely...Be careful.

---

### Post by Xiong Chiamiov on 2008-06-01
When dealing with GRUB issues, [SuperGrubDisk]("http://supergrubdisk.org") is your friend.

---

### Post by The Oz on 2008-06-01
> **spiderbatdad said:**
> Try startx to get into your GUI. Then run: ```
gksu nautilus
```
This will open your file browser with admin privileges. You'll be able to navigate and edit system files freely...Be careful.

I did that.  It does not show the menu.lst that I see in terminal.
If I try to copy the backup of menu.lst to the directory and force it, It wont work either.
input:cp -f menu.lst /media/hda/boot.grub/menu.lst
output: cp: cannot create regular file `/media/hda/boot.grub/menu.lst': No such file or directory

This still confuses me.

What is the super grub disk?  I guess i will try it out...

---

### Post by drs305 on 2008-06-01
> **The Oz said:**
> 
input:cp -f menu.lst /media/hda/boot.grub/menu.lst
output: cp: cannot create regular file `/media/hda/boot.grub/menu.lst': No such file or directory



Typo: you are missing a /   

/media/hda/boot**/**grub/menu.lst

---

### Post by spiderbatdad on 2008-06-01
> **The Oz said:**
> I did that.  It does not show the menu.lst that I see in terminal.
If I try to copy the backup of menu.lst to the directory and force it, It wont work either.
input:cp -f menu.lst /media/hda/boot.grub/menu.lst
output: cp: cannot create regular file `/media/hda/boot.grub/menu.lst': No such file or directory

This still confuses me.

What is the super grub disk?  I guess i will try it out...

Not sure what you mean here. I'm assuming you are doing a normal boot (not live cd) and running startx....Then gksu nautilus. The menu.lst you see there is your menu.lst...and hopefully a backup. Simply right click and rename each, appropriately.

---

### Post by The Oz on 2008-06-01
> **drs305 said:**
> Typo: you are missing a /   

/media/hda/boot**/**grub/menu.lst

Oops!  Maybe that's why I can't copy!

EDIT: nope, still get the same error...

@ spiderbatdad:
If you read the rest of the thread, you can see that the only way I can boot an OS is with the live CD.
In nautilus I can not see the menu.lst in /boot/grub Only in terminal.
The menu.lst I was trying to copy is a backup on my flash drive.
I can not right click and rename anything to menu.lst in the /boot/grub folder because of a broken "invisible" file.
Is there some sort of app that scans the partition for errors and repairs them because this is what I think I need

---

### Post by logos34 on 2008-06-01
do like Xiong said above and get Super Grub Disk.  Hopefully it will allow you to boot into ubuntu (it doesn't even require the presence of a menu.lst).

Then generate a new menu.lst with

sudo update-grub

---

### Post by spiderbatdad on 2008-06-01
supergrub sounds like a way to go, but there seems to be something fundamentally wrong with the cp command you've been trying. Like not specifying complete paths and correct file names....ie,

```
sudo cp -p /media/hda/boot/grub/menu.lst.bak /media/hda/boot/grub/menu.lst
```

where menu.lst.bak is replaced by the actual name of the backup file you have.

Or if you are in /grub as a working directory, you may only need the file name in each case:
sudo cp -p menu.lst.backup menu.lst

---

### Post by The Oz on 2008-06-01
I still get the same error.  Anyways, I always type my cp command like that, and it works.

I'm just going to try supergrub and see if it works

---

### Post by The Oz on 2008-06-01
So, I tried SGD, but my computer kept rebooting when it asks me to selct partition, so I gave up on that...

Managed to boot up windows through a recovery CD.  I tried to delete the  menu.lst file, but It says the file is corrupted, and it is impossible to erase.  If I can get rid of that file I think I can fix this.  Could sombody PLEASE tell me how I can get rid of the corrupted menu.lst file!!

---

### Post by spiderbatdad on 2008-06-01
how about ```
sudo rm -f menu.lst
```

---

### Post by logos34 on 2008-06-01
if you can't remove the file with spiderbatdad's command above I'd run a filesystem check (which at some point should have been forced automatically by the system):

sudo fsck /dev/sda2

(replace sda2 with your ubuntu root partition)

Other than than I'd start considering backing up your ubuntu files to windows partition and reinstalling

---

