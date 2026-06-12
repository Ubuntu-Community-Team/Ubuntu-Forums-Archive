---
title: "External hard drive problem after upgrade"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Futant on 2012-07-02
Hello, a couple of days ago I upgraded from 11.10 (via cd, choosing the 'keep programs' option, which didn't work, had to re-install everything) to 12.04, and it's mostly working fine, but I seem to have a problem with my external hard drive. I can access everything on it fine, but two things are causing problems:
 1) When I start Deluge it says 'Cannot access Volume: Permission denied', which is strange as it then goes on to work fine. I'm just a bit puzzled about this. 
 2) A more immediate problem is that when I re-installed the video editor LiVES and try to start it it says 'LiVES was unable to use the temporary directory /media/Volume/LiVES/livestmp/  Please check the  setting in  /home/futant/.lives and try again.' 
 I'm guessing this has something to do with the permission thing, or leftover information causing problems, but I don't know what to do about it. Also, there is no .lives folder, just an empty folder called .lives-dir. I have tried un and re-installing several times, to no avail. Someone please help, I need this program for my work! Thanks in advance.

---

### Post by sudodus on 2012-07-02
Have you changed the mount-point of the external drive from what it was before upgrading to 12.04?

Is it mounted to ```
/media/Volume
``` or to something else?

Maybe it is enough to make a link.

---

### Post by Futant on 2012-07-02
Hey thanks for your reply, looks like you're on to something... Checked the 'media' folder, there is something called 'Volume' which says 'you do not have the permissions necessary to view Volume' when I try to open it, then there is 'Volume_' which I can open fine and access my external hard drive. So what now?

---

### Post by sudodus on 2012-07-02
Try to access 'Volume' with superuser privileges

```
sudo ls -l
``` or
```
gksudo nautilus
``` if you are using the file browser Nautilus

And check why you have both 'Volume' and 'Volume_'. Is 'Volume' in your [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT] file? Or do you have two drives with the same label?

---

### Post by sudodus on 2012-07-02
If you post the result of the following commands it might be easier to help.
```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```

---

### Post by Futant on 2012-07-02
> **sudodus said:**
>  And check why you have both 'Volume' and 'Volume_'. Is 'Volume' in your [FONT=Courier New][SIZE=3]/etc/fstab[/SIZE][/FONT] file? Or do you have two drives with the same label?

Hello, just checked fstab file and there is no mention of Volume. I only have the one external drive, and haven't intentionally changed anything. I will post the output from the commands you mentioned in a moment. I don't know what I'm doing so bear with me! Thanks for helping

---

### Post by Futant on 2012-07-02
Here is the output from the three commands: ```
futant@futant-Dell-System-XPS-L502X:~$ sudo fdisk -lu Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 4096 bytes I/O size (minimum/optimal): 4096 bytes / 4096 bytes Disk identifier: 0x07f2837e     Device Boot      Start         End      Blocks   Id  System /dev/sda1              63      208844      104391   de  Dell Utility Partition 1 does not start on physical sector boundary. /dev/sda2   *      208896    41168895    20480000    7  HPFS/NTFS/exFAT /dev/sda3        41168896   780639209   369735157    7  HPFS/NTFS/exFAT /dev/sda4       780640254   976771071    98065409    5  Extended Partition 4 does not start on physical sector boundary. /dev/sda5       968601600   976771071     4084736   82  Linux swap / Solaris /dev/sda6       780640256   960428031    89893888   83  Linux /dev/sda7       960430080   968591359     4080640   82  Linux swap / Solaris  Partition table entries are not in disk order  Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes 255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xe74754cc     Device Boot      Start         End      Blocks   Id  System /dev/sdb1            2048  2930274303  1465136128    7  HPFS/NTFS/exFAT
```  ```
   futant@futant-Dell-System-XPS-L502X:~$ sudo blkid /dev/sda1: SEC_TYPE=&quot;msdos&quot; LABEL=&quot;DellUtility&quot; UUID=&quot;3030-3030&quot; TYPE=&quot;vfat&quot;  /dev/sda2: LABEL=&quot;RECOVERY&quot; UUID=&quot;92E2E7B1E2E7982D&quot; TYPE=&quot;ntfs&quot;  /dev/sda3: LABEL=&quot;OS&quot; UUID=&quot;00B8457CB8457168&quot; TYPE=&quot;ntfs&quot;  /dev/sda5: UUID=&quot;34deed57-638f-4e19-9b00-12b883cd2cf9&quot; TYPE=&quot;swap&quot;  /dev/sda6: UUID=&quot;8cdae8ac-a26e-4173-8b7f-7e819dabb621&quot; TYPE=&quot;ext4&quot;  /dev/sda7: UUID=&quot;70e46981-fbf7-42c9-8be5-b35834b338f2&quot; TYPE=&quot;swap&quot;  /dev/sdb1: LABEL=&quot;Volume&quot; UUID=&quot;A27CA9FD7CA9CC7B&quot; TYPE=&quot;ntfs&quot; 
```  ```
 futant@futant-Dell-System-XPS-L502X:~$ df Filesystem      1K-blocks      Used Available Use% Mounted on /dev/sda6        89748080  12786932  72466456  15% / udev              1999588         8   1999580   1% /dev tmpfs              802748       964    801784   1% /run none                 5120         0      5120   0% /run/lock none              2006864       112   2006752   1% /run/shm /dev/sdb1      1465136124 929749356 535386768  64% /media/Volume_
``` Oh, and this is my fstab file, not sure what I'm looking for here? 
 # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # #                 proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda6 during installation UUID=8cdae8ac-a26e-4173-8b7f-7e819dabb621 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda5 during installation UUID=34deed57-638f-4e19-9b00-12b883cd2cf9 none            swap    sw              0       0 # swap was on /dev/sda7 during installation UUID=70e46981-fbf7-42c9-8be5-b35834b338f2 none            swap    sw              0       0

---

### Post by sudodus on 2012-07-02
> **Futant said:**
> Here is the output from the three commands:
```
futant@futant-Dell-System-XPS-L502X:~$ sudo fdisk -lu
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility Partition 1 does not start on physical sector boundary.
/dev/sda2   *      208896    41168895    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41168896   780639209   369735157    7  HPFS/NTFS/exFAT
/dev/sda4       780640254   976771071    98065409    5  Extended Partition 4 does not start on physical sector boundary.
/dev/sda5       968601600   976771071     4084736   82  Linux swap / Solaris
/dev/sda6       780640256   960428031    89893888   83  Linux
[COLOR="SeaGreen"]/dev/sda7       960430080   968591359     4080640   82  Linux swap / Solaris[/COLOR]
Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe74754cc

   Device Boot      Start         End      Blocks   Id  System
[COLOR="red"]/dev/sdb1            2048  2930274303  1465136128    7  HPFS/NTFS/exFAT[/COLOR]

```
```

futant@futant-Dell-System-XPS-L502X:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda2: LABEL="RECOVERY" UUID="92E2E7B1E2E7982D" TYPE="ntfs"
/dev/sda3: LABEL="OS" UUID="00B8457CB8457168" TYPE="ntfs"
/dev/sda5: UUID="34deed57-638f-4e19-9b00-12b883cd2cf9" TYPE="swap"
/dev/sda6: UUID="8cdae8ac-a26e-4173-8b7f-7e819dabb621" TYPE="ext4"
[COLOR="SeaGreen"]/dev/sda7: UUID="70e46981-fbf7-42c9-8be5-b35834b338f2" TYPE="swap"[/COLOR]
[COLOR="red"]/dev/sdb1: LABEL="Volume" UUID="A27CA9FD7CA9CC7B" TYPE="ntfs"[/COLOR]

```
```

futant@futant-Dell-System-XPS-L502X:~$ df
Filesystem      1K-blocks      Used Available Use% Mounted on
/dev/sda6        89748080  12786932  72466456  15% /
udev              1999588         8   1999580   1% /dev
tmpfs              802748       964    801784   1% /run
none                 5120         0      5120   0% /run/lock
none              2006864       112   2006752   1% /run/shm
[COLOR="Red"]/dev/sdb1      1465136124 929749356 535386768  64% /media/Volume_[/COLOR]

```
Oh, and this is my fstab file, not sure what I'm looking for here? ```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
              proc            proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8cdae8ac-a26e-4173-8b7f-7e819dabb621 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34deed57-638f-4e19-9b00-12b883cd2cf9 none            swap    sw              0       0
[COLOR="SeaGreen"]# swap was on /dev/sda7 during installation
UUID=70e46981-fbf7-42c9-8be5-b35834b338f2 none            swap    sw              0       0[/COLOR]
```

1. The external device has the label ***Volume*** and it is mounted at ***Volume_*** for some reason. Maybe there is something (a directory, a file or bad permissions) at /media/Volume, so that it cannot be mounted. Can you check that?

If you cannot change the mount point, maybe you can change the references in programs to 'Volume_' instead of 'Volume', but this would be an ugly work-around.

2. You have two swap partitions, but you need only one. So I suggest that you delete /dev/sda7 and remove the reference to it from /etc/fstab.

*. But first of all ***backup*** all important data before doing anything with partitions!

---

### Post by Futant on 2012-07-02
There is indeed a directory at media/Volume, but I can't access it - I don't have the required permissions. Do I need to get rid of /media/Volume in favour of /media/Volume_? if so, how to get permission? And how do I change the mount point? At the moment I can't get into LiVES to change the reference - at this stage I would be happy with an ugly workaround because I only have a couple of hours of internet access left today. 
 Have I ended up with two swap partitions because of the upgrade? To delete /dev/sda7 do I boot the cd and use the partition editor there?

---

### Post by sudodus on 2012-07-02
Try the GUI way with superuser privileges
```
gksudo nautilus
```

and check whatever is at [FONT="Courier New"][SIZE="3"]/media/Volume[/SIZE][/FONT] and delete it unless you want to back it up to some other place.

---

### Post by sudodus on 2012-07-02
The other answers:

> **Futant said:**
> There is indeed a directory at media/Volume, but I can't access it - I don't have the required permissions. Do I need to get rid of /media/Volume in favour of /media/Volume_? if so, how to get permission? And how do I change the mount point? At the moment I can't get into LiVES to change the reference - at this stage I would be happy with an ugly workaround because I only have a couple of hours of internet access left today.

If you manage to wipe /media/Volume, you should not need the ugly work-around.
> 
 Have I ended up with two swap partitions because of the upgrade? To delete /dev/sda7 do I boot the cd and use the partition editor there?
Yes, and yes :-)

---

### Post by Futant on 2012-07-02
Thankyou so much for your help! Problem is sorted :D And I understand the workings of Ubuntu a little (very little!) bit better. Now to hopefully not mess everything up messing with partitions... One more thing, will having two swap partitions be a problem or is it just ungainly? Thanks again!

---

### Post by sudodus on 2012-07-02
> **Futant said:**
> Thankyou so much for your help! Problem is sorted :D And I understand the workings of Ubuntu a little (very little!) bit better. Now to hopefully not mess everything up messing with partitions... One more thing, will having two swap partitions be a problem or is it [COLOR="Red"]just ungainly[/COLOR]? Thanks again!
1. Congratulations :KS

2. [COLOR="red"]Just ungainly[/COLOR] with 2 swap areas. The second one is mounted and available but probably never needed (so waste of drive space).

And if you are happy (for the moment), please click on **Thread Tools** at the top of this thread and mark this thread as SOLVED

---

