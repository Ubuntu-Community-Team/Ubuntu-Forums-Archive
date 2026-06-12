---
title: "[SOLVED] problem reconnecting other internal hard drives after successful installatio"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by lmkwak on 2008-09-05
Hi everyone!

My first newbie question:

I have successfully installed Ubuntu, and it works! However, I did this by opening my computer, unplugging the two internal hard drives that my Windows install file was not on (but lost of music, files, etc that I didn't want to lose), and installing it over Windows. I wanted to completely remove Windows as it was filled to the brim with Trojans and spyware.

After playing around on Ubuntu for a few days I wanted to have a go at connecting my hard disks again. I tried my external hard drive first, no problem there. Then I plugged both internal drives in, but the computer wouldn't restart. I unplugged one, leaving one plugged (named TITAN), restarted, and started up normally. The computer 'sees' TITAN under 'places', but when I try to look at the files on it I got the following error message:

Cannot mount volume
Unable to mount the volume 'TITAN'

I took a screenshot of the full message, but I don't know how to add it to the post, so in short it goes on to explain that I can choose to unmount it in Windows (which I dont have on the desktop anymore, and as it is an internal drive, I cannot do with my laptop) or I can use the 'force' option for my own responsibility, typing in 
mount -t ntfs-3g /dev/sdb1/media/TITAN -o force
but when I hit enter I am told only root can do that. I don't know how to log in as root, and I am not sure I want to as I might do something wrong...

What should I do? Any suggestions are welcome, I am very new to the console and to Linux in general.. but very eager to learn!

Thanks in advance, 
Laura

---

### Post by Shazaam on 2008-09-05
Put sudo in front of the mount command (needs to be run as root).

---

### Post by lintoon on 2008-09-05
Yeah, just run the command the error message is telling you but type sudo in front of it.  Type your normal password in when prompted (That's if you are the original user which was created on the system).

You say it's your first newbie question so I presume you may not know how to type it in.  You need to open the "Terminal".

Go to the "Applications" menu then select "Accessories" and then "Terminal"

---

### Post by lmkwak on 2008-09-05
Thanks Shazaam for the super speedy response!

I put sudo in front of it, and it did something, but I am not sure what. The disk is visible again though! Great!!!! Many thanks!

But I am still curious to know what I did... After giving the password I get the following:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Is it a help file for the 'mount' command? If so, why does it show, did I somehow ask for it? Do I still need to do something else to finalise the process?

---

### Post by lmkwak on 2008-09-05
> **lintoon said:**
> 
You say it's your first newbie question so I presume you may not know how to type it in.  You need to open the "Terminal".


Its my first newbie question because there are already so many answers. Questions I had before had searchable answers!

But thanks anyway!

---

### Post by lmkwak on 2008-09-05
Problem solved, but the question is still open...

---

### Post by Jack M. on 2008-09-05
That is the mount help file, yes. It's supposed to only appear when you run
```
mount -h
```
but if the drive is working fine, I wouldn't worry about it. By the way, ```
man (commandname)
``` provides a more comprehensive manual for most commands.

---

### Post by lmkwak on 2008-09-05
Okay, thanks for the explanation! And I really appreciate the 'manual' tip, I will definitely be using that before doing anything as root, which still scares me a little because of the potential damage I could!

---

