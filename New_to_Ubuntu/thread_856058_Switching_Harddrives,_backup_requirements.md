---
title: "Switching Harddrives, backup requirements?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by jeepin on 2008-07-11
I'm purchasing a larger HDD. I have got my Ubuntu configured how I want it, all the plug ins working, all hardware properly configured, and the 3rd party software I downloaded installed great...
  What is the best way to do a switch to this new HDD? Will I have to re-download everything via synaptic that I did, the updates, etc?? Will I have to reconfigure all of my apps (FF, etc)? Or is there a way to just backup, reload and have everything the same? Should I use SBackup? 
  Thanks! Sorry for the many questions but this is the first time I have had to switch HDD's with Ubuntu and I really don't want to start from scratch. 
 -J

---

### Post by hyper_ch on 2008-07-11
you could try this:

(1) boot from the live cd
(2) make sure everything is unmounted
(3) run this command
[code]
sudo dd if=/dev/sdx of=/dev/sdy
[code]
if --> input file --> hence the harddisk you currently have installed ubuntu upon
of --> output file --> hence the new harddisk

That should produce a 1:1 copy of the content on the harddisk.

Afterwards try to boot from the new one (unplug the original one). If that works, then start again from the live cd and adjust the partition size.

That shouldn't take too long and it should work - but I never tried it myself.

---

### Post by jimmy the saint on 2008-07-11
get hirem's boot cd or the gparted-clonezilla boot cd and use a bit of software to clone the drive.  clonezilla is probably the best route since there are not any legal issues involved.  Essentially, it will make an image of the contents of your current drive and transfer it to your new drive.  I did this without a hitch several times.  Issues can arise is you are using the drive to dual boot windows though.  Just make sure that you clone the disk and not a partition.

---

### Post by tinny on 2008-07-11
Hi

At the very least you should back up your /home/ directory. This folder holds all of the config type information for your systems users.

I cant really think of a way in which you can also migrate all your applications a system config stuff. You could try and Ghost your install and then restore it when you have the new drive installed.

Also, you could have a look at this How too.

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by Zack McCool on 2008-07-11
OR, you could get really crazy...   Install the new HD as a slave (or a second drive if it is SATA).  Partiition it and format it, mount it to /media/home temporarily.  Copy everything from /home to /media/home.  Now unmount the drive, mount it at /home and see if everything works.

As long as everything is OK, you can unmount it, delete everything under /home (keep a backup, though), update your fstab so it mounts on boot, and your new drive is now all usable space in your home directory...

---

### Post by jimmy the saint on 2008-07-11
I stand by clonezilla.  Install the new HD, note the make and size, and let clonezilla do the rest.  This is a graphical tool, with menus, buttons and such that is made to do just this.  It is easy, fairly self explanitory, and if you search online, you can find plenty of step-by-step walkthroughs with photos and everything.  Follow the KISS method and you will be fine!!

---

### Post by jeepin on 2008-07-11
Thanks. I think I will go with either the Live CD boot and do what Hyper_ch said OR what Jimmy the saint says, with the clone software...however, I do run dual boot on this drive (the one running ubuntu), what issues can I expect, and how shall I prevent them? By being sure im cloning the disk and not the partition save me from this possible issue? Thanks.

---

### Post by zxscooby on 2008-07-11
I would read up on using DD to clone the disk before i tried it.
a small mistake could wipe your data.

---

### Post by jimmy the saint on 2008-07-11
The issue lies in the fact that, if you get too creative in the cloning process, partitons can change.  This means that grub will be looking at a partion to load that is no longer the partition which contains the OS.  This shouldn't be an issue if you don't change the partiions though.  When I cloned my dual boot drive I think the files that Ubuntu uses to boot were no longer being found properly.  I know there is a solution to this, but I wound up reformating the drive and scrapping my windows partion and running windows from a virtual machine instead so I didn't have a chance to resarch them.  That happened with my acronis True Image CD though.  Maybe since clonezilla is designed for linux that won't be an issue for you though.

---

### Post by forger on 2008-07-11
I'd suggest to boot with the latest ubuntu hardy heron 8.04.1 live cd
then System > Administration > Partition Editor

Part 1:
**[COLOR="Red"]DO NOT MOUNT YOUR DRIVES UNTIL THIS IS DONE[/COLOR]**
Copy your partitions from one hard disk the other.
1) on the **upper right** corner you choose your hard drive device
2) select your partition > press Copy
3) on the **upper right** corner you choose the other hard drive device
4) select the space to use (unallocated?) and press Paste.

If you're happy with the changes that you're about to do, press **Apply**
It's going to be a long procedure, so go do something else until it's done.

**When it's done**, i.e. gparted says it has finished

Part 2:
1) Applications > Accessories > Terminal
```
ls -l /dev/disk/by-uuid/
```
This shows you the uuid used in /etc/fstab

2) Then mount (from your **new** hard disk) the copied root partition (usually on the desktop or in Places > right-click on icon > mount)
Open the partition to browse its files/folders
Head to folder etc > file fstab and open it to edit it.

3) Edit the device UUID to match the new device UUID
i.e. 
> # /dev/sda1
UUID=0bd7b6de-d497-489f-87ab-ec905e5938f5 /               ext3    errors=remount-ro 0       1
You will change **UUID=0bd7b6de-d497-489f-87ab-ec905e5938f5 ** and use the appropriate one from part 2 (1)

Shutdown the live ubuntu now, disconnect the old hard disk

---

### Post by jeepin on 2008-07-11
Thanks Forger..
 Do you believe this will cause an issue with the MBR?
 And when I begin your "Part 2", im assuming it will still boot the old HDD right? That way I can access terminal to get the UUID.....well i guess it would because its not mounted yet (the new one).
 We'll see how it goes....

---

### Post by hyper_ch on 2008-07-11
well, copying by dd if=/dev/sdx of=/dev/sdy will make a 1:1 copy of the harddisk incl. the mbr...

the only thing that will change if you resize partitions afterwards then their UUID will change... so you have to take care of that in the /etc/fstab file - if partitions are referred by their UUID

---

### Post by forger on 2008-07-11
grub is the least of your problems:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

either from the live cd or even super-grub-disk can help you fix that :)

---

### Post by markbuntu on 2008-07-11
Why bother?
If you can add another hard drive without being required to remove the old one, why do you need to move everything to it. Is the old one failing?

If you just need more room for your personal/media files, just put the new one in, format it, and move your personal/media directories into it.

No need to turn this into an experiment in hard drive mirroring.

---

