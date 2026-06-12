---
title: "The disk drive for /media/sda1 is not ready yet or not present...Press S to skip..."
date: 2012-11-05
forum: New to Ubuntu
---

### Post by spiritualbird on 2012-11-05
I am a ubuntu beginner and it is my first post in ubuntuforum. 
I am using ubuntu for about about 3/4 months. I installed ubuntu 12.04 LTS in separate partition. Recently I change my Windows 7 to Windows 8 and after that I lost boot option(means I lost bootloader). However, somehow I restore and upgrade grub and now I can log on to ubuntu. But a slight problem still exists. While log on to Ubuntu it appears:

The disk drive for /media/sda1 is not ready yet or not present. Continue to wait, or Press S to skip mounting or M for manual recovery.

In this case, waiting results nothing, Pressing S temporary solve the problem(but appears everytime while booting) and let me log in, and Pressing M starts command line which I cannot understand.

It is for your information that, sda1 is the windows 8 system drive. 

Here is my fdisk information:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72a980e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   137482221    68740087    7  HPFS/NTFS/exFAT
/dev/sda2       137484331   393816063   128165866+   f  W95 Ext'd (LBA)
/dev/sda3       393822208   685275135   145726464    7  HPFS/NTFS/exFAT
/dev/sda4       685275136   976773119   145748992    7  HPFS/NTFS/exFAT
/dev/sda5       137484333   362360129   112437898+   7  HPFS/NTFS/exFAT
/dev/sda6       362360832   393816063    15727616   83  Linux

```

And below find blkid info:
```
/dev/sda1: UUID="FC72A05A72A01C00" TYPE="ntfs" 
/dev/sda3: UUID="9E2361E723821A3B" TYPE="ntfs" 
/dev/sda4: LABEL="mS world" UUID="A22BAFF07BC3EDFF" TYPE="ntfs" 
/dev/sda5: UUID="01CC71DE177F0320" TYPE="ntfs" 
/dev/sda6: UUID="713495a1-f39f-4e99-a15b-ddd92a5a5c57" TYPE="ext4" 

```

Please give me solution how to solve this problem while booting. I have found a similar solution in: 

[http://ubuntuforums.org/showthread.php?t=1742933&page=2](http://ubuntuforums.org/showthread.php?t=1742933&page=2)

But the command instruction in #11 thread was too hard for me to understand how to implement. So, it could not solve my problem. 

So please use step by command approach because I have not been an advanced ubuntu user yet. 

I found ubuntu as an amazing OS, I am falling in love with it. Unity is awesome, a way better than metro. Dash is a pure innovation, HUD too. Waiting to see more innovation from ubuntu....

---

### Post by mcduck on 2012-11-05
check your */etc/fstab* file, which is where mounting of drives is configured. Most liekely the windows update changed the UUID of the sda1 partition, and you just need to edit the fstab to use the correct UUID (which you can see in your blkid output).

---

### Post by spiritualbird on 2012-11-06
> **mcduck said:**
> check your */etc/fstab* file, which is where mounting of drives is configured. Most liekely the windows update changed the UUID of the sda1 partition, and you just need to edit the fstab to use the correct UUID (which you can see in your blkid output).
Thank you mcduck for your instruction. I have gone through this, and yes there was another UUID in fstab file, I replace the old ID with the new one from blkid output. After that I restarted ubuntu but problem still exists. It says:

An error occured while mounting /media/sda1
Press S to skip or M for manual recovery

So the new error message was not the one for which I wrote for solution. 

Before I edit fstab, I can mount my sda1 drive manually by clicking the disk in nautilus. But now I cannot mount it by clicking it says:

Unable to mount 70 GB Filesystem
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/sda1

Please give me a solution of the newest problem...

---

### Post by mcduck on 2012-11-06
> **spiritualbird said:**
> Thank you mcduck for your instruction. I have gone through this, and yes there was another UUID in fstab file, I replace the old ID with the new one from blkid output. After that I restarted ubuntu but problem still exists. It says:

An error occured while mounting /media/sda1
Press S to skip or M for manual recovery

So the new error message was not the one for which I wrote for solution. 

Before I edit fstab, I can mount my sda1 drive manually by clicking the disk in nautilus. But now I cannot mount it by clicking it says:

Unable to mount 70 GB Filesystem
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/sda1

Please give me a solution of the newest problem...
unless the mount options in fstab include the "user" option, any drive configured there requires root permissions to mount.

Anyway, could you post your fstab file here, so we can take a look?

---

### Post by spiritualbird on 2012-11-07
Here is my fstab file : [http://bit.ly/myfstab](http://bit.ly/myfstab)

Here I saw a thing, When I restart my windows 8 and then select ubuntu from bootmanu there shows no error. But if I shutdown Windows and then start and select ubuntu to boot it shows the error.

---

### Post by Gerardo Duran on 2013-04-23
Hi, I had the same problem but now it is solved:
write at Terminal : gksu gedit /etc/fstab
In the file, delete the lines in relation with your disk drive or write a "#" before the corresponding line

---

### Post by Hodevah on 2013-04-24
> **Gerardo Duran said:**
> Hi, I had the same problem but now it is solved:
write at Terminal : gksu gedit /etc/fstab
In the file, delete the lines in relation with your disk drive or write a "#" before the corresponding line

I have a very similiar problem (on my laptop) to what is being talked about in this thread. So I would also like to ask that in respect to your post an placing a '#' before the media drive in the aforementioned file, are you talking about the media drive that is not being mounted or that is having trouble being mounted? Because if so, does this not then prevent the drive from being mounted and therefore unable to mount it? Please explain because I also have this same problem.

---

### Post by spiritualbird on 2013-08-06
I have found a solution to this problem. The problem arises for dual booting Ubuntu with Windows 8. Problem is in Windows 8 *Fast Startup* mechanism. It not only makes the system drive of Windows inaccessible from Ubuntu but also causes data loss in shared NTFS file system. So, to fix the issue, just turn off Fast Startup and Hibernate from Power Option. Go through the link: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)  Follow Option 3 (disabling hibernate will automatically disable Fast Startup). It will be OK inshaAllah. 

You can also read this forum post: [http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

