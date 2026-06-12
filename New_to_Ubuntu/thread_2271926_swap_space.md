---
title: "swap space"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by hmiersch on 2015-04-02
hi. 
I just ran gnome system monitor and it told me something like "swap not available". When i installed ubuntu, i created a 50GB partition for virtual memory (the machine has 16GB RAM). so why isn't it available? and what can i do to make it available?

---

### Post by Bashing-om on 2015-04-02
hmiersch; Well ....

Too soon to say, but we start the look'n process:
```

sudo fdisk -lu
sudo blkid
cat /etc/fstab

``` to see what is set up and what is called for.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-04-02
Hi Bashing

@OP
That you been running without swap, tells me you do not really need it.  It seems to be a never ending discussion, but unless you use hibernate,  I say 2G of swap is enough.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=How+much+swap+do+I+need&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=How+much+swap+do+I+need&sa=Search&cof=FORID:9)

---

### Post by ajgreeny on 2015-04-02
> 50GB partition for virtual memoryIs that what you mean should be your swap?  How did you make the "virtual memory" as you call it?

I don't think I've ever seen a forum user with potentially such a large swap partition; as v3.xx says you would probably be fine with 2 - 4GB unless you must hibernate, but that is hardly worth the palaver these days as Ubuntu boots so quickly from cold; almost as fast as coming out of hibernation in my experience so I don't bother with it.

---

### Post by hmiersch on 2015-04-03
ok, lets see...

sudo fdisk -lu gives me the following output:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20479       10239+  ee  GPT
/dev/sda2   *       20480    97677311    48828416   82  Linux swap / Solaris
/dev/sda3        97677312   976771071   439546880   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398931968 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029163  1953514581+  ee  GPT

Disk /dev/mmcblk0: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders, total 62333952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *        8192    62333951    31162880    b  W95 FAT32



when i type sudo blkid , first nothing happens for a couple of seconds (is that nomal?) and then this appears:

/dev/sda3: UUID="a85d8347-78aa-49e4-ace6-8467f6df8ed1" TYPE="ext3" 
/dev/sdb1: LABEL="EFI" UUID="67E3-17ED" TYPE="vfat" 
/dev/sdb2: UUID="8bd3ac76-557d-3a2f-a513-27c67eb9f1f4" LABEL="Media files" TYPE="hfsplus" 
/dev/mmcblk0p1: LABEL="SD32" UUID="BF0E-19EC" TYPE="vfat" 


and finally, cat /etc/fstab gives me this:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=a85d8347-78aa-49e4-ace6-8467f6df8ed1 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
#UUID=c4f7f1c5-af04-4a0e-b1f2-b5186205b5bd none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by Bucky Ball on 2015-04-03
You don't need more than 2Gb of /swap, unless you wish to hiberante, in which case same amount as your installed RAM (16Gb). 

Please use code tags for terminal out put. See last link in my signature. Thanks. ;)

---

### Post by hmiersch on 2015-04-03
well, i thought that my swap space was working until system monitor told me otherwise. like i said, i have 16GB RAM, so maybe thats why i didn't have any problems. as for the size of my swap partition, changing it would not give me any benefits without a lot of work (reinstalling everything) so for now i'll leave it as it is, overkill or not. but i'd still like to get it to work, because otherwise it'll be just a waste of space...

---

### Post by sudodus on 2015-04-03
I see cryptswap. So you have 'encrypted home'. There is a bug, that makes cryptswap fail.

See this link [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

I suggest that you use 'encrypted disk' instead.

See this link (the instructions how to install and test it) [http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/91445/testcases/1451/results](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/91445/testcases/1451/results)

---

### Post by hmiersch on 2015-04-03
BTW, i went into gparted, and it gave me the following info on my swap partition:

Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda2 is missing

---

### Post by sudodus on 2015-04-03
It is possible to change the system and use normal swap with encrypted home (to overwrite the cryptswap with a normal swap space), but it will be a security hole. If you do not want to re-install (and get 'encrypted disk') it is better to continue without swap.

---

### Post by hmiersch on 2015-04-03
> **sudodus said:**
> 
See this link (the instructions how to install and test it) [http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/91445/testcases/1451/results](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/91445/testcases/1451/results)

i guess this means i have to re-format and re-install. that is exactly what i want to avoid. isnt there another way?

---

### Post by sudodus on 2015-04-03
It might be possible to create and run 'a new' cryptswap every time you boot the computer. Try to automate it with a shell-script (that you create yourself), but it is not convenient. Maybe the best solution is to continue without swap.

The cryptswap bug is in the process of debugging, so maybe cryptswap will work soon, if you can wait.

---

### Post by hmiersch on 2015-04-03
> **sudodus said:**
> See this link [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

does that work in 14.04? and do i have to do that every time I boot or will the effect be permanent?

---

### Post by sudodus on 2015-04-03
I have tested various tweaks, but the current bug-fix in Vivid kills all those tweaks. I think and hope there is a better bug-fix in the pipe-line, but I cannot guess, when it will be available. Maybe 'my method' still works in 14.04.1 LTS. The bug-fix will probably 'trickle down' to that version after some months, which might make the situation better or worse. See this link, if you want more details

[http://ubuntuforums.org/showthread.php?t=2266912&page=3&p=13244000#post13244000](http://ubuntuforums.org/showthread.php?t=2266912&page=3&p=13244000#post13244000)

---

### Post by hmiersch on 2015-04-25
> **sudodus said:**
> I see cryptswap. So you have 'encrypted home'. There is a bug, that makes cryptswap fail.

See this link [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

i tried this:

> 
 - Find the swap device that was meant to be used in "sudo fdisk -l" (it  should say "Linux swap" in the last column), remember the device name  (something like "/dev/sda5")
 - Find the UUID in /etc/crypttab (the long alphanumeric ID after UUID=)
 - Run "sudo mkswap -U 1234... /dev/sda5", replacing "1234" with the above UUID, and /dev/sda5 with the device name from step 1.
 - Edit /etc/crypttab to append ",offset=1024" in the fourth (last)  column of the cryptswap1 line; ensure that there is *no space* between  the "cipher=aes-cbc-essiv:sha256" and the appended option. If there is a leading "#" in the file, remove that too.
 - If there is a leading "#" in /etc/fstab in the line starting with /dev/mapper/cryptswap1 line, remove that.
 - Run "sudo update-initramfs -u".


but it didn't help :-(. when booting i still get the message that the cryptswap disk isn't ready yet, and system monitor still tells me "swap not available"
is there something else i have to do? did i do something wrong?

---

### Post by sudodus on 2015-04-25
Encrypted home with cryptswap is ***successfully debugged, fixed and works in the new version 15.04*** of Ubuntu and the Ubuntu flavours (Kubuntu, Lubuntu, Xubuntu ...). I have tested it in Lubuntu 15.04.

I hope and think the bug-fix will trickle down to the long time support version with the next point release 14.04.3 LTS.

---

### Post by hmiersch on 2015-04-28
today i tried again to get my swap space going. but 

sudo mkswap -U <UUID> <device> 

only gives me an error: device or resource busy. what the ****?? how can it be busy when it's not being used? i guess this is why it didn't work the last time i tried...

do i get this error because the swap partition is on the same actual HD as the one i boot from?

so what can i do about that?

---

### Post by mattharris4 on 2015-04-28
> **ajgreeny said:**
> Is that what you mean should be your swap?  How did you make the "virtual memory" as you call it?

I don't think I've ever seen a forum user with potentially such a large swap partition; as v3.xx says you would probably be fine with 2 - 4GB unless you must hibernate, but that is hardly worth the palaver these days as Ubuntu boots so quickly from cold; almost as fast as coming out of hibernation in my experience so I don't bother with it.

I don't trust hibernate on a computer anyway, I had a bad experience with that once years ago using Win XP where I lost data so I would say don't bother with either hibernation or a swap area.  The only other use for swap is if you run out of RAM as it will use that part of your hard drive as RAM (but will also slow your computer to a crawl at best or freeze it up at worst).  It sounds like you don't need it.  I do set up a swap area equal to my RAM but only so if a RAM module fails I can save and shut down rather than have my computer freeze up completely for sure (requiring a manual shutdown) and lose even more data because of it.

I don't know but I suspect the 50GB is set aside for a virtual machine intended to run other OSes without affecting the main OS installation.  If this person does not intend to run a VM IMO he should really clean this up, I don't know if he can just expand his data partition into it or if he would have to backup his documents, wipe the drive and reinstall the OSes he intends to use (starting with Windows if needed and then the Linux OS).  The answer to that depends on what is before that partition -- if it is swap or OS and not his data partition before the VM partition it would likely require a wipe and reinstall. Of course if he has 500GB or more of data partition already this is less important as the only reason to clean this up is so he can use it for data when necessary.

---

### Post by sudodus on 2015-04-29
> **hmiersch said:**
> today i tried again to get my swap space going. but 

sudo mkswap -U <UUID> <device> 

only gives me an error: device or resource busy. what the ****?? how can it be busy when it's not being used? i guess this is why it didn't work the last time i tried...

do i get this error because the swap partition is on the same actual HD as the one i boot from?

so what can i do about that?

The command you describe should work. Did you 'swapoff' or unmount the device where you try to create swap? It should be possible even if it is on the same drive as you have booted from. Maybe there is a swap entry in the file **/etc/fstab**, and you should remove or 'comment away' that entry. But I'm not sure what is the problem. It is hard to help with a system that is buggy. If you really want cryptswap, I suggest that you try the new version 15.04, where the bug is fixed.

---

### Post by hmiersch on 2015-04-29
the weird thing is tat during boot i still get the "cryptswap disk not available" message but system monitor no longer says "swap not available". instead it says "0 bytes (0%) of..." 
That number doesn't surprise me because i'm using like 10% of my total memory, so there's no need to use swap. but it all makes me realize what a piece of bloatware OSX really is. and windoze too, probably.
does this mean it works now? but then why do i still get the message during boot?
i guess one way to find out is to make a VM with LOTS of ram assigned to it, like 16GB or more...

---

### Post by sudodus on 2015-04-29
Yes, that would be a good way to provoke swapping.

---

