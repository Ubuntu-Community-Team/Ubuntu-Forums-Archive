---
title: "Unable to boot due to a full boot drive"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by maggiemonic on 2012-09-20
hello!

i have been having some issues since updating to 11.10 last night. many files were not able to install, which i believe is why the system wouldn't reboot (i get a  "disk drive for / is not ready yet or not present" error on the ubuntu screen). anyhow, i was able to run some commands to install those missing pieces. this is causing me a new problem of being unable to boot still because that 120MB or so of installation (i believe) filled up the boot drive. 

current situation: i can only boot in recovery mode or else i get stuck (meaning frozen... cannot click OK) at "in low graphics mode" alert. this has occurred once in the past and the solution was to delete files via the command line. however, when i use the rm /home/stupidfiles i get a "rm: cannot remove '/home/stupid' : read-only file system. i also cannot run sudo apt-get autoclean or anything to free up space. 

when i do attempt to boot in recovery mode i get the "disk drive for / is not ready yet or not present" error and then press M for manual fix, which gives me a command line. 

any input is much appreciated!

-nicole

---

### Post by carl4926 on 2012-09-20
Boot the live CD
Take a look at your file system

It's possible you could clean up some from here or even chroot in to your installed system.

But IMO, assuming you made the obligatory backup before the upgrade. I'd be planning a clean install

---

### Post by maggiemonic on 2012-09-20
ah, yes... i should also have mentioned that i am using a netbook and do not have a cd drive or a bootable flash. 

is there any way i can work around this issue without needing to boot from a flash drive?

---

### Post by carl4926 on 2012-09-20
> **maggiemonic said:**
> ah, yes... i should also have mentioned that i am using a netbook and do not have a cd drive or a bootable flash. 

is there any way i can work around this issue without needing to boot from a flash drive?

I'm not sure.
Wait and see if anyone has a bright idea

---

### Post by BicyclerBoy on 2012-09-20
Ubuntu updates during a release tends to build up a huge pile of old kernel images/packages..

I have to keep manually un-installing kernel packages on my netbook because the SSD is so small & kernel updates come every couple days here..

It is a pity your system is non-functional.
The boot process starts with the filesystem read only, it stays that way if things are broken.
You could try to remount as read write.
sudo mount -o rw,remount /

df -h
(is the disk really full)

One way to see how many kernel images you have is look at the grub boot screen (shift key during boot) or running this in terminal:
ls -al /boot/

Danger:
You can manually remove some of the old images if you are **really really** desperate..
Remove matching pairs of initrd.* vmlinuz-* then run:
sudo update-grub
Note: you must not remove all the images..it is a good idea to leave 2 recent versions & one of the oldest ones.

---

### Post by Wim Sturkenboom on 2012-09-20
// EDIT 1: maybe I should read and comprehend your post first before posting :(
// EDIT 2: but it should actually work; just tested it on 10.04 with 'root shell without networking'

Standard the system keeps some space available for the root user (unless you changed the reserved space on the partition). So boot into recovery mode and drop to a root shell. 

Next cleanup your system. The first step will probably be
```

sudo apt-get clean

```
which will clear apt's cache.

Next you can run
```

du -h --max-depth=1 /

```
to see which directories are big (if you're no longer root, use sudo).

---

### Post by shreepads on 2012-09-20
How can you be certain that the source of the problem is a full boot drive?

Also does the system support booting from a USB attached flash drive? If not (and there is no DVD drive) how did you get Ubuntu installed on it..

It may be a disk hardware problem, in which case you really should be leaving it alone and create a bootable flash drive from another system and boot using that and recover you data first... (assuming you can boot from a flash drive).

---

