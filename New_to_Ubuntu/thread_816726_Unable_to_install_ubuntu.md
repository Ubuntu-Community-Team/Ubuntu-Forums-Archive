---
title: "Unable to install ubuntu"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Kronie on 2008-06-03
hi guys, i just got the ubuntu disk today and i have a bit of a problem installing it.. please follow the link for more detailed information
[http://www.linuxforums.org/forum/ubuntu-help/123038-newb-needs-your-help-cant-install-ubuntu.html#post593967](http://www.linuxforums.org/forum/ubuntu-help/123038-newb-needs-your-help-cant-install-ubuntu.html#post593967)

also, heres the screnshot of the error i get when i try to access one of the partitions from live CD

[IMG]http://ipicture.ru/uploads/080603/e23Px2FL71.png[/IMG]

---

### Post by laffinet on 2008-06-03
Gathering from your link you don't really care if you can not boot into windows anymore as long as you're able to install Ubuntu and then access those windows drives. Is this correct ?

Can you explaing in detail what happens when you try to boot into windows ? 

Also, which partitioning option did you choose when trying to install Ubuntu ?

---

### Post by .nedberg on 2008-06-03
The error tells you what is wrong and what to do. The NTFS volume did an "unclean" shutdown.

Mount it with
```

sudo mount -t ntfs-3g /dev/sda1 /mount/XP -o force

```
make sure /mount/XP exists first

---

### Post by oedha on 2008-06-03
make sure you have shutdown your windows properly :)

---

### Post by Kronie on 2008-06-03
aait, so ive been messing around with the live CD(to be honest, i could use it as my permanent OS 0_o) and i tried to mess around with the partitions.. so i broke up one of my existing NTFC partitions into 3 pieces and made the new one of them linux swap(1 gig) and another one ext3 with mount point /target, right now its on 82% of installation process...

---

### Post by Kronie on 2008-06-03
ait so i installed ubuntu, its workind flawlessly and so far i love it..
the only problem that's left is to make my XP partition readable for ubuntu.(Vista one shows up fine)

**.nedberg**
i tried to use ur code and thats what i got.. to be honest i have absolutely 0 idea about what it says here..
```

kron@kron-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /mount/XP and other Crap -o force
[sudo] password for kron: 
Sorry, try again.
[sudo] password for kron: 
Sorry, try again.
[sudo] password for kron: 
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

```

---

### Post by cariboo on 2008-06-03
Did you truly enter this line:

```
sudo mount -t ntfs-3g /dev/sda1 /mount/XP and other Crap -o force

```

and expect it to work?

Jim

---

### Post by canthus13 on 2008-06-03
You need quotes around any filename or volume name with spaces in it, like so:

> sudo mount -t ntfs-3g /dev/sda1 "/mount/XP and other Crap" -o force

--Me

---

### Post by akiratheoni on 2008-06-03
> **cariboo907 said:**
> Did you truly enter this line:

```
sudo mount -t ntfs-3g /dev/sda1 /mount/XP and other Crap -o force

```

and expect it to work?

Jim

Hey, no need to be mean here. At least explain what he did wrong, you're doing nothing to help.

The error is that when you use filenames or directory names with spaces in them, you need to put a quote around the ENTIRE path. So that command should be:

> sudo mount -t ntfs-3g /dev/sda1 "/mount/XP and other Crap" -o force

---

### Post by Kronie on 2008-06-03
**cariboo907**
ofcourse i didnt expect it to work -_- i dont even know what any of those commands mean, and i thot that nedberg just made a "shortcut" for the whole name... but i tried it just the way he wrote it and thats what i got.
```
kron@kron-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /mount/XP -o force[sudo] password for kron: 
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

---

### Post by Kronie on 2008-06-03
**canthus13**
**akiratheoni**
thanx a lot for the tip ;) will keep it in mind.. 
i tried the "fixed" version of the code...
```
kron@kron-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 "/mount/XP and other Crap" -o force 
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

---

### Post by canthus13 on 2008-06-03
Hmm... Are you still able to boot into windows? If so, then do it, and then shut down windows cleanly.  That may fix the issue.  If not, you might be forced to use something akin to Paragon Disk utilities to recover whatever is left on the partition, and then format the partition and start over.

--Me

---

### Post by rrcs on 2008-06-03
If you need a screenshot of e.g. an error message, and don't want your desktop background, other windows etc. to show:

1. Click on the window you want a screenshot of to activate it.
2. Click Alt+Print Screen.
3. Save screenshot as per usual.

Sorry I have no help for your actual issue, but due to all the crossing out of IM conversations, etc., I thought you might find this helpful for future reference :)

---

### Post by Kronie on 2008-06-03
awwww... T_T i am screwed here.. i dont have effin dvd buener or floppy drive for the partition magic boot utility... well anyway thanx for help, i really apreciate it :D

---

### Post by _sphinx_ on 2008-06-03
Make sure that you have not Hibernated your XP, I faced a similar kind of problem when I hibernated my windows partition and was trying to access that partition from ubuntu.

---

### Post by .nedberg on 2008-06-03
> **Kronie said:**
> **canthus13**
**akiratheoni**
thanx a lot for the tip ;) will keep it in mind.. 
i tried the "fixed" version of the code...
```
kron@kron-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 "/mount/XP and other Crap" -o force 
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

There is something wrong with your NTFS partitions. You will not be able to mount them.

Have a look here for a way to "fix" it:
[http://ubuntuforums.org/showthread.php?t=455565](http://ubuntuforums.org/showthread.php?t=455565)

---

### Post by Kronie on 2008-06-03
**rrcs**
lawl thanx allways wanted to have that feature in windows :D

---

### Post by Kronie on 2008-06-03
**.nedberg**
the windows XP actually shows up in the GRUB but i cang get onto it. when i select windows XP, it brings on the loading screen (windows flag with loading bar below it) and then right after it finishes the loading it restarts the PC...

---

### Post by .nedberg on 2008-06-03
> **Kronie said:**
> **.nedberg**
the windows XP actually shows up in the GRUB but i cang get onto it. when i select windows XP, it brings on the loading screen (windows flag with loading bar below it) and then right after it finishes the loading it restarts the PC...

Well, Grub only see its own config file and shows you the option to boot windows. Windows tries but fails because of the error with the partition.

Have a look at the thread I linked to, it tells you how to restore mbr with the windows cd (will remove grub). That way you might get your windows back. Afterwards you can recover grub if you want to.

---

### Post by canthus13 on 2008-06-03
I was kind of afraid of that.  The only utility I've found that could recover files from an NTFS partition in that condition was Paragon Disk Manager.  If you can get ahold of a copy of that, you can at least recover whatever you need before you reformat it.  You may be able to get to it with some other rescue CD, but I know Paragon will work.  Good luck.

--Me

---

### Post by .nedberg on 2008-06-03
Not sure if testDisk will work, but a friend of mine had luck with it. Get it here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by canthus13 on 2008-06-03
Ooooo... Thank you.  Something to add to my USB drive. :)

--Me

---

### Post by Kronie on 2008-06-03
thank you guys for helping me out! :D ill carry on by myself after now i guess :) well have bizillion more questions, and so little time to find answers for them....

---

