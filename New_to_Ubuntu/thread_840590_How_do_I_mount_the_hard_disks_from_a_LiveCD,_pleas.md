---
title: "How do I mount the hard disks from a LiveCD, please?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Tedel on 2008-06-25
Hello,

Please, I need a prompt answer: One of the PCs at the office broke down, so the idea was to download a Linux LiveCD, open the file manager, **backup all the important files** and then reinstall Windows on the machine.

However, I cannot mount hda1 nor hda2 from the Ubuntu Hardy LiveCD. Can someone tell me how to do it? Installing Hardy on the target computer is not an option. I must rescue the files first.

Thanks a lot.

---

### Post by drs305 on 2008-06-25
Added and Edited: I may not have a complete picture of what you want. Are these windows partitions or linux ext3 partitions? 

Once you have booted to the liveCD desktop, for ext3 partitions:

Open a terminal.
... Accessories, Terminal.

```

sudo mkdir /temp
sudo mount /dev/hda1 /temp

```

The files should be visible on /temp
You can make another mount point and repeat this for hda2

---

### Post by Tedel on 2008-06-25
No, it didn't help. It seems it's not present in the list of available media. any way to change the fstab?

---

### Post by avtolle on 2008-06-25
Wondering if this might help. Once booted into the Live CD, hit Alt+F2. In the box provided, input gksudo nautilus, and OK (or whatever the command is). Nautilus should come up, and in the left panel, there should be a listing of various things, one of which may be computer or file system. If computer, click on it, and then select file system (which should be the Windows hdd). Right click to open, and if all is well, you should see a listing of files, etc. If file system comes up, do the same thing, that is, click on it and a browser should open showing the files. Now, you hopefully should be able to use Nautilus to copy these files, etc., to external media. If there is a permission problem (hopefully there won't be), right click the file/folder and see if you can change the permissions associated with the same to allow access to them. 

As Elmer Fudd would say, "Be vewy, vewy careful", as you are running in root, and can really screw things up if you err. Proceed slowly, with caution, and you should be able to get the files off.

---

### Post by drs305 on 2008-06-25
Edited: avtolle's post made while I was typing will be much more direct should it work!

What type of partitions/drives are you trying to mount? Were these partitions /drives mounted and available in ubuntu previously? I didn't really get an answer if we were trying to access windows or ubuntu drives/folders.

If they were listed in fstab, you can review your fstab file by mounting the ubuntu / (root) partition in the manner described previously and then running:
```
cat /temp/etc/fstab
```

If they were ntfs or vfat files we will see that in fstab (if they are listed).

---

### Post by sam1948 on 2008-06-25
if u'r windows was shut down in appropriately then the hard drives are flaged as closed or something like that 
to get over it u can start windows installation from a cd
choose R for repair whenever u get to it
and when u'll get to the command line 
type:> shutdown 
or 
:> reboot 
then upload the live cd 
Good luck!

---

### Post by unutbu on 2008-06-25
Please post

```
sudo fdisk -l
```

There is a chance that your partitions are being registered as /dev/sda1, /dev/sda2 instead of /dev/hda1, /dev/hda2. fdisk will show us what Hardy sees as your hard drives.

Also, if machine was halted abruptly, you may need to run fsck to correct filesystem corruption errors.
I'm not sure how to run fsck from a Windows recovery CD. If you know, great, otherwise google for instructions or post which version of Windows is on the machine and someone here will surely tell you how.

---

