---
title: "permission denied for old files."
date: 2013-01-09
forum: New to Ubuntu
---

### Post by bruce86 on 2013-01-09
My problem, sectionalized to reduce reading in case i included useless info.

**Preamble:**
While i have been using Ubuntu for a year, it was set up for me by someone else, and i have no understanding of the technical aspects.  So i am posting my problem in here first, just in case I'm a moron and am missing something obvious.  If it requires more specialized help i will repost in the appropriate board at a later time.

**The Story:**
My computer randomly shut down one day, and whenever i tried to restart it, it would go past the first boot page (the one that says "press f10 to boot") and then the screen would stay black.  So i used my ubuntu boot disc in order to boot the computer so i could try and recover some of the important files (i have 100gb of data, but most is just bs i don't care about.  some of it, however, are family pictures and home movies).  So i boot with the CD and my hard drive is available as a partition, yay!  But while it says the hard drive has 111gb in use, only 37gb of it are recognized by nautilus.  of those 70+gb unrecognized are my important files.  

**The Nitty Gritty:**
So, while i am able to open some of the files, others say i do not have the permission to access them.  Also, when i look at properties it says "Contents unreadable" and wont give information about number or size of files.  I would like to know how to gain permission, and access to these files.  I do believe they are still there because it recognizes that 111gb are in use.


**Specs:**
While i had updated my system before the crash, i had not yet updated to ubuntu 12.04,  the CD boot is ubuntu 11.10.


Thank you for any help you are able to offer.

---

### Post by lukeiamyourfather on 2013-01-09
The files probably need to have the owner changed. If you're familiar with the command line (or want to learn it) use the chown command.

> sudo chown -R luke:luke Music

Using "sudo" at the front means to do the command as the root user (required to change owner when you're not the owner, when asked for a password enter your password). The "-R" means recursive so it will do everything in the directory and subdirectories, the "luke:luke" is the user and the group you want to be the owner (usually your username and a group of the same name). The last thing, "Music" is the folder to change owner on, this could be a single file too. If you want to know more about the command use this command.

> man chown

That will bring up the manual for chown (push "q" to exit the manual). There might be a way to do this without the command line but I don't have a machine in front of me to test with.

---

### Post by leviteo on 2013-01-09
Hey,

First of all we must check if your data is not corrupted. 

I believe this following is a good start point to you:

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

You will have to use the command line :)

BR,
Leví

---

### Post by lukeiamyourfather on 2013-01-09
That's a good point, corrupted files is a possibility (in that case seek help from a specialist if the files are really important). My suggestion of changing the owner is based on my experience when reinstalling or grabbing files from foreign disks.

---

### Post by bruce86 on 2013-01-09
Ok, like i said, i am not all that savvy, and am probably just making a stupid mistake.  But, i went to the link leviteo sent because it seemed a good idea to check for corruption first, and it's a mounted drive (i assume because it gives me an option to unmount it), so i tried number 5 for mounted drives.

The command it suggests is :

# mount | grep "/dev/sd*"

I tried it like that with no results, and then i changed the "/dev/sd*"
to:
 "/media/73b718b5-65dc-4825-bf4f-d6ed1770d822" and 
"/media/73b718b5-65dc-4825-bf4f-d6ed1770d822*"

because the drive is under "media" on the main home file, and the drives name is 
"73b718b5-65dc-4825-bf4f-d6ed1770d822" for some reason.

I know it's probably  just a stupid mistake that i'm making, and i know it's really frustrating to deal with someone like me and i really appreciate the help.

---

### Post by lukeiamyourfather on 2013-01-09
No need to mount the drive if you can already navigate to it in the file browser. Generally speaking Ubuntu will automatically mount drives for you, like when you insert a USB drive or click on a drive from the file manager.

---

### Post by leviteo on 2013-01-11
Hi,

As you already see some part of the HD on Nautilius your HD is already mounted.

Check that with:

cat /proc/partitions 

In my machine:

major minor  #blocks  name
   8        0  265975808 sda -> My HD
   8        1  265451520 sda1 -> First partition
   8        2          1 sda2 -> Second partition
   8        5     521216 sda5 -> Third partition
  11        0      56056 sr0

After that, uses the command to check the corrupted data.

Leví

---

### Post by bruce86 on 2013-01-15
ok, so i tried what Levi just suggested, and then used the info to run a file check like the geekstuff site that was posted suggested.  and this popped up, and i was hesitant to continue without checking first.

---

### Post by leviteo on 2013-01-15
Hey Bruce,

DONT RUN fsck on mounted filesystem. Use the command to check your partition. 

Then umount the sda2 and run fsck.

---

### Post by leviteo on 2013-01-15
When you run the ls -l command in these directory what is the result?

---

### Post by leviteo on 2013-01-15
Did you try to open the files with sudo?

---

