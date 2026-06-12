---
title: "How to mount and format floppy disks in Ubuntu 9.10"
date: 2009-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by impyre on 2009-12-05
I've had a lot of trouble with this one, especially regarding blank "IBM Formatted" disks. The auto-mount utility for floppy disks in gnome had trouble with clean disks. Getting into "Windows" disks isn't remarkably easy either. Many people will say floppies are extinct, and I do agree for the most part, but anyone who has built a Windows system with SATA hard drives prior to Vista's debut will understand why you may still need an occasional FDD.

To mount MS-DOS formatted floppies, you will need to mount them from the Terminal (found in applications>accessories>terminal).

sudo mount -t msdos /dev/fd0 /mnt/floppy

You need sudo to access the device, and the -t option tells the system to look for a msdos filesystem. The /dev/fd0 is your floppy drive, (though it could be /dev/fd1... you can check by browsing the /dev folder if you want to make sure). 

The last piece, /mnt/floppy, is the point where you want to mount the device to. You will need to create it manually. There's probably already somewhere you can mount it, but this will probably be easier and quicker. 

A couple of notes here: 

a) once it's been mounted in your mount-point you cannot use nautilus (EG: right click and copy or remove or past) to modify what's on the disk. For some reason it doesn't play nice. You could probably make custom commands using nautilus' built-in editor, but it will be easier to "rm" "cp" "mv" from within the /mnt/floppy to remove, copy, and move files... respectively.

b) when you are finished, ESPECIALLY if you've written new content to the floppy, make sure you un-mount the drive using this command:

sudo umount /dev/fd0

If you do not unmount it, your changes will not stay. This is because the changes are stored in memory, and written when you umount. That also means that if you filled a disk up, it may take a minute for the light to go out. When it's done, you'll get your prompt back inside the terminal, and the floppy will calm down. It's then safe to remove your disk.

So that's how you get into and modify a windows floppy disk, but what if you want to build a windows-compatible disk from a blank "IBM Formatted" disk? You can use mformat from the mtools suite. It should already be installed on your computer.
The command to format a standard 1.44MB floppy disk is as follows: 

sudo mformat -f 1440 A:

The 1440 is the number of bytes, and the A: specifies the floppy drive. It may require a different drive letter, but I'd try that one first. That will format a disk to msdos filesystem using FAT 16. Afterwards, you can access and modify it using the above steps.

I'm still learning myself, so please let me know if I need to change or add something here.

---

### Post by ron999 on 2009-12-06
Hi
Yes, I've just used the method you suggested.
It seems OK.
**mformat** wasn't installed on my machine already.
But I've installed **mtools** from the repo, it's part of that package.
:D
Also I can access the disks, when mounted, using **sudo** nautilus from the terminal.

---

### Post by _george on 2009-12-09
Hi. I have little bit another problem.
I don't have the floppy drive in my computer and i want to remove floppy from anywhere.
I tried comment the corresponding row in /etc/fstab, but it's not helps. Floppy is not mounted but stay in my computer and Places :-/
I have Ubuntu 9.10. May be someone can help me, because i only half year in Ubuntu ..

---

### Post by mahiyar on 2009-12-14
Thanks impyre, your tip really helped me.

---

### Post by joconnor on 2010-01-26
This post is in reply to impyre's post.

As a normal user you can do:

mount /dev/fd0

which should mount the floppy filesystem at the default mount point which should be /media/floppy0.

In other words you do not need to elevate your rights for this form of mount.

With the floppy drive mounted like this, you can use nautilus as per normal.

---

### Post by Matt2015 on 2010-01-26
I've been trying to mount a disk image created by vmware from within an ubuntu (8.04) virtual machine and after reading this thread and looking around I've made some progress.

Initially I couldn't mount the disk image at all, as it wasn't formatted.

This was resolved by using either

[FONT=Courier New]mkdosfs /dev/fd0[/FONT]

or

[FONT=Courier New]mke2fs /dev/fd0[/FONT]

The first formats the disk in msdos format, the second ext2 format.

After that I could mount the msdos disk by simply

[FONT=Courier New]mount /dev/fd0[/FONT]

as in the post above, which indeed mounts to /media/floppy0

To mount the ext2 format I had to use

[FONT=Courier New]sudo mount -t ext2 /dev/fd0 /media/floppy[/FONT]

to achieve the same thing (floppy seems to be a symbolic link to floppy0)


Ultimately I'm trying to put redboot on a disk image, so that I can boot a virtual machine to play around with eCos and embedded linux.

---

### Post by srwilde on 2010-03-08
I think I love you.  I hate WinXP and its lack of RAID drivers.

---

### Post by RT236 on 2010-03-16
Thanks!!!  I had been having trouble trying to format a floppy as KFloppy does not work. We use them in cameras here for quick pictures and formatting floppy disks was getting to be a problem. Cameras are too expensive to toss.

---

