---
title: "Help mounting ntfs partition automatically. Fstab file type confusion."
date: 2014-07-07
forum: New to Ubuntu
---

### Post by benawhile on 2014-07-07
I have a dual boot XP installation with a shared ntfs partition.
 My old system was 12.04 and I have done a fresh install to 14.04 with manually created partitions.
 I am sure that both times I let the installation program create the shared partition as FAT and later I reformatted it to NTFS in the disk utility,( although I have just noticed that this now doesn't seem to present a list of file types.)

 As with the first 12.04 installation I have had problems with automatic mounting of the ntfs partition.  
 As before I am trying to fix it using fstab, but am finding it more difficult this time for some reason.  
 

 In terminal:
 

 fdisk -l sees /dev/sda7 as “HPFS/NTFS/exFAT”
 

 blkid sees it as UUID="421C9FB21C9FA009" TYPE="ntfs"  
 

 fstab sees it as # /media/sda7 was on /dev/sda7 during installation  
 UUID=9685-328A  /media/sda7     vfat    utf8,umask=007,gid=46 0       1
 (even when not mounted)
 

 finally, disk utility sees /dev/sda7 as
 

 NTFS — Mounted at /media/ben/421C9FB21C9FA009
 

 or  

 Partition type HPFS/NTFS
 Contents NTFS — Not Mounted
 

 Why does each method show a different file type? Can anyone see what I have done wrong and recommend the best fix, using fstab?
 

 Why does fstab say “# /media/sda7 was on /dev/sda7 during installation “ ?
 

 I didn't see this message when I edited fstab the previous time. What does it mean? Is this a new phrase introduced between 12.04 and 14.04?

---

### Post by Bucky Ball on 2014-07-07
Install ntfs-3g and ntfs-config. Run 'NTFS configuration tool' and set mount permission for sda7. That will rewrite your fstab. Reboot and see if it mounts ok.

fstab is not dynamic. It doesn't change unless you change it. Makes no difference whether partitions are mounted or not. It is a set of static instructions. ;)

---

### Post by mooreted on 2014-07-08
Create a mount point for your NTFS partition. This is an example, you can name it what you want:

sudo mkdir /mnt/Windows

Then edit your fstab:

sudo nano /etc/fstab

Using the example:

/dev/sdb7 /mnt/Windows ntfs-3g defaults 0 0

Test to see if it mounts:

sudo mount -a

---

### Post by Impavidus on 2014-07-08
Your FAT partitions had UUID (=some kind of ID that stays fixed even when drives are swapped or partitions moved) 9685-328A. That is the UUID the installer put in fstab. After reformatting to NTFS the UUID changed to 421C9FB21C9FA009. This is the UUID that you have to put in fstab. I assume ntfs-config can do it for you, although it isn't very hard to do it manually.

Also make sure you have a sensible mountpoint. Any empty directory will do, as long as it exists, but names like /media/ben/421C9FB21C9FA009 or /media/sda7 are not very practical.

---

### Post by Bucky Ball on 2014-07-08
> **Impavidus said:**
> I assume ntfs-config can do it for you, although it isn't very hard to do it manually.



Although it may be for some with no instructions how. Example of what Impavidus is referring to:

```
sudo blkid
```

This will give you all the details you need for the fstab entry. Open another terminal and:

```
sudo nano /etc/fstab
```

... to open the fstab file. 

Copy and paste the correct UUID numbers from the 'sudo blkid' terminal into the appropriate places in the '/etc/fstab' terminal. Reboot. ;)

But if you don't fancy the terminal, yes, the ntfs-3g route will do it for you.

---

### Post by benawhile on 2014-07-08
Thank you for this, people, not sorted yet though.

 OK, I did what Bucky Ball said first. I didn't instasll ntfs-3g, just ntfs-config. Is that OK?

 Not sure if I did it right. First time I ran ntfs-config with the drive already mounted. The drive was pre selected, so I just clicked to do it. Then I read on another thread that I should do it with the drive unmounted so I unmounted it and  ran again, this time I just got the write support window showing everything mounted. BTW the partition I am concerned with is just the ntfs shared data partition, not the Windows one.
 Now from desktop disk utility shows it as already mounted before I open it in nautilus file manager, which it didn't do before.  

 *Problem is on boot I was still presented with the message:*
 *The disk drive for /dev/sda7 is not ready yet or not present. Click S to skip.*

 Mooreted. I don't understand why I should have to create a mount point,  wasn't there a (complicated) one already there at   
 NTFS — Mounted at /media/ben/421C9FB21C9FA009
 ?
 Impavidus, I don't understand this bit:
 “Any empty directory will do, as long as it exists” How do I choose a practical name, and how do I find an empty directory that exists?

 Also now fdisk -l does/shows nothing, is that because I installed ntfs-config?

 Bucky I am happy to work in terminal and to try to crack fstab. Like I said, I cracked it last time by research and didn't have to post on the forum. At least I don't think I did, I can't find any old posts!  

 Here are the previous and present fstab files:
 Previous:

 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 # / was on /dev/sda6 during installation 
 UUID=f85564b7-39f9-4942-9540-17dc58eabd01 /               ext4    errors=remount-ro 0       1 
 # /media/sda7 was on /dev/sda7 during installation 
 UUID=9685-328A  /media/sda7     vfat    utf8,umask=007,gid=46 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=58071999-d824-4e9b-a226-d519ed882674 none            swap    sw              0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
 

 After ntfs-config:

 # /etc/fstab: static file system information. 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
  
 #Entry for /dev/sda6 : 
 UUID=f85564b7-39f9-4942-9540-17dc58eabd01    /    ext4    errors=remount-ro    0    1 
 #Entry for /dev/sda7 : 
 UUID=421C9FB21C9FA009    /media/ben/421C9FB21C9FA009    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0 
 #Entry for /dev/sda1 : 
 UUID=8410C40010C3F768    /media/sda1    ntfs-3g    defaults,locale=en_GB.UTF-8    0    0 
 UUID=9685-328A    /media/sda7    vfat    utf8,umask=007,gid=46    0    1 
 #Entry for /dev/sda5 : 
 UUID=58071999-d824-4e9b-a226-d519ed882674    none    swap    sw    0    0 
 /dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0

---

### Post by Bucky Ball on 2014-07-08
Could you perhaps shutdown the machine and reboot. Still get that message? Your fstab is looking fine to me.

Think what we are trying to collectively say, is that you should create another mountpoint (directory), say /media/sda7, and mount the partition there. Make the directory, for instance:
```

sudo mkdir /media/sda7
```

... and change the line for sda7 to:

```
#Entry for /dev/sda7 :
UUID=421C9FB21C9FA009 /media/sda7 ntfs-3g defaults,nosuid,nodev,locale=en_GB.UTF-8 0 0 
```

Take note: You could change the mountpoint name /media/sda7 to /media/fruitcake; whatever you fancy, doesn't matter, just as long as the fstab matches it. Not sure why you would want to mount the partition in /media/ben/***. The partitions should be mounted directly in the /media partition (media/***). 

PS: Looks like you marked you Win partition, sda1, to be mounted at boot also.

---

### Post by benawhile on 2014-07-08
I did try a reboot, no joy.

Then following your instructions I got this in terminal:

ben@ben-MS-7253:~$ sudo mkdir /media/sda7
[sudo] password for ben: 
mkdir: cannot create directory ‘/media/sda7’: File exists
ben@ben-MS-7253:~$ 

BUT by the way, I incorrectly quoted the boot message. It actually says /media/sda7 is not ready yet, not /dev/sda7.

The complicated mount point was some kind of default that the machine came up with.

Presumably I don't need the windows to mount at boot but I can't change anything in the ntfs window now, sda1 and sda7 are checked in the advanced configuration list and I can't uncheck either. There is only an undo button greyed out and a "close" button.

---

### Post by Bucky Ball on 2014-07-08
Open /etc/fstab and put a hash (#) in front of the Win partition boot line (comment it out):

```

#Entry for /dev/sda1 :
# UUID=8410C40010C3F768 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0 
```


I have just noticed something. 

```
#Entry for /dev/sda7 :
**UUID=421C9FB21C9FA009 /media/ben/421C9FB21C9FA009 ntfs-3g defaults,nosuid,nodev,locale=en_GB.UTF-8 0 0**
#Entry for /dev/sda1 :
UUID=8410C40010C3F768 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
**UUID=9685-328A /media/sda7 vfat utf8,umask=007,gid=46 0 1 **
```

I'm confused so possibly the system is at boot also. You best check your UUIDs again with 'sudo blkid' and fix up the fstab by deleting the entry that is incorrect. You still have your old boot line in there as well which is trying to mount at /media/sda7. So you have applied the ntfs-3g to the obscure system created line, but the last line here is still vfat.

Perhaps make it look like this, at a guess:

```
#Entry for /dev/sda7 :
**UUID=421C9FB21C9FA009 /media/sda7 ntfs-3g defaults,nosuid,nodev,locale=en_GB.UTF-8 0 0**
#Entry for /dev/sda1 :
# UUID=8410C40010C3F768 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0

```

... if that is the correct UUID for /dev/sda7.

---

### Post by benawhile on 2014-07-08
That was the fix I needed, you have solved the problem for me, thanks.
Why does there have to be a hash at beginning of both lines for the windows fstab entry?
What narks me is that I have done two dual boot installs in the same pattern now, both involved manual partitioning and a shared ntfs partition, and both threw up the same or similar problem, and I don't know why.
It must have been something I did wrong from the time I reformatted the fat to ntfs. That was when the mount point was changed to that long one. I originally had it as /media/sda7.
There must be something I have done wrong from the start.

---

### Post by Bucky Ball on 2014-07-08
The hash marks mean the lines are ignored. You mean these two Windows lines?

```
#Entry for /dev/sda1 :
# UUID=8410C40010C3F768 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

The first line, '#Entry for /dev/sda1 :' is wholly and solely informational. It serves no purpose in the boot other than so you know what is going on in fstab. You could remove completely (in fact, without the # boot would likely throw another error as the system wouldn't understand what it means). 

For the second line, which is actually a command and not purely informational, '# UUID=8410C40010C3F768 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0', grub simply ignores this line as it is commented out with a #. Again, you could remove both lines without issue rather than commenting them out with a #.

As for why the Ubuntu install created fstab the way it did, unsure. :-k ;)

---

### Post by benawhile on 2014-07-09
[FONT=arial]I now have a theory about how I got into this mess:                         
[SIZE=2]
In the original fstab there is no entry for sda1, the Windows OS partition, so when I ran ntfs-config it saw the sda1 windows partition as an ntfs system and created an entry for it, but also found the original mount point, now unused, /media/sda7, that I created for the shared FAT partition during installation, and  so ntfs-config created the second entry as well.
[/SIZE]
 [SIZE=2]At some stage after installation of 14.04 when I reformatted the shared partition to ntfs I must have allowed the system to create the new "/media/ben/421C9FB21C9FA009" mount point

So at least three things went wrong. The wrong mount point was created for the shared partition when it was reformatted, and the original mount point was left without a drive, which is why I got the message on boot that the disk drive for /media/sda7 was not ready or present, then I ran ntfs-config, which created an unnecessary fstab line for the windows OS partition, and then it created a second one as well.

This doesn't explain everything. for example if the /media/sda7 mount point was allocated to the windows OS partition, why was I still getting the "not ready yet or not present" message on boot? But it gives me an idea what to look out for in the future. I wi[/SIZE][SIZE=2]ll need to watch what happens when reformatting the FAT partition and make sure the same mount point is kept for it.[/SIZE][/FONT]

Dual boot with a shared ntfs partition created manually seems such an ideal method for starting to use ubuntu, but is really fraught with problems that could be avoided. What doesn't help is that the ubuntu installation system doesn't seem able to create ntfs partitions, only FAT. Maybe it would be better to set up the partitions first with gparted?

---

### Post by Bucky Ball on 2014-07-09
> **benawhile said:**
> [FONT=arial] Maybe it would be better to set up the partitions first with gparted?

Or second. Install Windows at the start of the drive on a primary partition of about 40Gb. It will probably spew out a couple of other smaller ones. Then boot the Ubuntu installer, launch Gparted and create an extended partition with the rest of the drive. 
Manual partition by clicking 'Something Else' when you get there during install. 

Install Ubuntu to 20Gb logical partition inside the extended partition and add a 2Gb /swap at the end of the partition/drive. Just avoid the NTFS primary partitions created by Windows. Make sure not ticked to use or format. 

Reboot and you should get the menu with both OSs available. Boot Ubuntu, launch Gparted, create an NTFS logical partition inside the extended one to share data. Done.

For future reference, that's how I'd go about it. Good luck and enjoy. ;)

---

