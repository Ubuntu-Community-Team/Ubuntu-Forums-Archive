---
title: "[SOLVED] File system check failed."
date: 2008-09-08
forum: New to Ubuntu
---

### Post by UltraRos on 2008-09-08
Hello people,

I installed ubuntu 7.10 a few weeks ago, last weekend it crashed somehow,
becouse I couldn't find a solution and I still had win-XP on it I tried to
reinstall ubuntu so that I had only one OS.

This didn't work, so I installed yesterday ubuntu over my win-xp partition.
result: = 2 times ubuntu installed 2 partitions.

then I upgraded my new installation to 8.04, (today) after that I tried to 
format my first (defective) installation (witch is called sda3).

When I boot at this moment I get the following message during the boot,
when the file system of sda4 (the new installation) is being checked.

===========================================================================

* Checking file systems...
1176

fsck 1.40.8 (13-mar-2008)
fsck.ext3: Unable to resolve 'UUID=88202516-902e-4382-9291-680daed83138'
fsck died with exit status 8
[RIGHT][[COLOR="Red"]fail[/COLOR]][/RIGHT]
* File system check failed.
A log is being saved in /var/log/fsck/checkfs
if that location is writable.
please repair the file system manually.

* A maintenance shell will now be started.

CONTROL-D will terminate this shell and resume system boot.

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: the: command not found
bash: dircolors: command not found
bash: command: command not found
bash: the: command not found
root@ultraros-desktop:~#

==========================================================================

When I press "CONTROL-D" or "Exit" or "Reboot" the system boots up
and I can use her, but I prefer to solve this so I can boot the normal way.

When I try to use the life-CD it doesn't work, my system doesn't boot from 
the life-CD anymore, although it worked yesterday and in my BIOS is booting 
from CD enabled.

Can someone please help me? or should I let 
my system feel the flat side of the road?

greetings UltraRos.

---

### Post by MegaJim on 2008-09-08
What does the log file (/var/log/fsck/checkfs) contain?

---

### Post by UltraRos on 2008-09-08
Hi MegaJim, thank you for trying to help,

the log file (/var/log/fsck/checkfs) contains

=============================================================================

Log of fsck -C3 -R -A -a 
Mon Sep  8 15:18:30 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=88202516-902e-4382-9291-680daed83138'

fsck died with exit status 8

Mon Sep  8 15:18:30 2008
----------------

=============================================================================

I hope this will help to find a solution.

---

### Post by bumanie on 2008-09-08
You should format the drive and then try to install, if you are not formatting the hard drive, youare tyring to put a new installation on a corrupted file system. If you just wnat to run ubuntu alone, from the live cd (before starting an installation) in terminal type sudo pat-get install gparted and then look undre Sytem --> administration --> Partition editor (Think that's the path  - at work on a windoze machine at present) and format the hard drive to ext3 filesystem.

---

### Post by MegaJim on 2008-09-08
it is likely that a UUID referred to in your fstab no longer exists (as it has been formatted/repartitioned, post your fstab

```
cat /etc/fstab
```

---

### Post by UltraRos on 2008-09-08
Ok but before I installed Ubuntu the second time I formatted the "NTFS" Win partition to an empty ext3 partition and and than installed ubuntu again, this morning my new ubuntu installation booted normally, it started acting this weard after I tried to format the other ext3 partition where the first ubuntu installation was on.

Do I still need to format and install again?

Thanks that you try to help me.

---

### Post by UltraRos on 2008-09-08
> **MegaJim said:**
> it is likely that a UUID referred to in your fstab no longer exists (as it has been formatted/repartitioned, post your fstab

```
cat /etc/fstab
```

Ok this is the result of ```
cat /etc/fstab
```

```
joop@UltraRos-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=620f6373-ceb4-43d2-a5d8-1f58338de857 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=88202516-902e-4382-9291-680daed83138 /media/hda3     ext3    defaults        0       2
# /dev/hda5
UUID=76D0374CD037123B /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=13DFA768E0039D61 /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda1
UUID=22de6324-6467-428b-9d2f-4074c5f39b8c none            swap    sw              0       0
# /dev/hda7
UUID=ed74fe7a-4758-4fbf-a753-0b2416d064c4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
joop@UltraRos-desktop:~$ 

```

---

### Post by bumanie on 2008-09-08
> **UltraRos said:**
> Ok but before I installed Ubuntu the second time I formatted the "NTFS" Win partition to an empty ext3 partition and and than installed ubuntu again, this morning my new ubuntu installation booted normally, it started acting this weard after I tried to format the other ext3 partition where the first ubuntu installation was on.

Do I still need to format and install again?

Thanks that you try to help me.

No, you should not need to if the drive/s have already been formatted to ext3. Post output as suggested above - quite possibly UUID issue as stated.

---

### Post by MegaJim on 2008-09-08
ok, this line "# /dev/hda3
UUID=88202516-902e-4382-9291-680daed83138 /media/hda3     ext3    defaults        0       2" has the possibly bad uuid entry, please post the output of this command

```
sudo vol_id --uuid /dev/hda3
```

---

### Post by UltraRos on 2008-09-08
it says ```
/dev/hda3: error opening volume
``` :(

---

### Post by MegaJim on 2008-09-08
thats ok, it has probably just been repartitioned to a different logical drive, as the partition no longer exists, just go ahead and delete the offending line from your fstab

```
gksu gedit /etc/fstab
```

remove the lines:

# /dev/hda3
UUID=88202516-902e-4382-9291-680daed83138 /media/hda3     ext3    defaults  0  2

then save the file, you should no longer get the fsck failure message

---

### Post by UltraRos on 2008-09-08
thank you!! this problem is solved now!! it works again.

---

