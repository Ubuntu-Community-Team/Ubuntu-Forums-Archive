---
title: "Power failure - can't boot into my linux - using &quot;try ubuntu&quot;"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by dcbouchard on 2012-06-03
Absolute newb.. Ubuntu 11.10 32 bit installed on Acer Aspire laptop... about once a month I reinstall Ubuntu from my Live USB which means heading back into here and finding java quick install links etc.  Reason for the multiple reinstall:
whenever ubuntu is not shutdown properly - power interruption - the system hangs.
I did run the memory test and the other option to rescue - hoping that it would find it's way!  I really don't want to do the re-install - I figure you would know the solution!
Right now I am using the "try Ubuntu" 
Please, I am a newb so I will need a bit of step-by-step - I have been learning to use terminal - cut/paste is wonderful thing!

---

### Post by oldfred on 2012-06-03
Whether Windows or LInux a power failure can cause file corruption. With Windows you would run chkdsk and with Ubuntu fsck (or e2fsck).

Must be unmounted so use liveCD or USB:
Try "e2fsck -f /dev/sdb1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.


#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

See man e2fsck for explanation of parameters if interested. If you have more than one ext4 partition you may have to run it one each partition (but not swap).

---

### Post by dcbouchard on 2012-06-03
e2fsck -f /dev/sdb1
In terminal or restart and as a grub command line?

---

### Post by dcbouchard on 2012-06-03
ubuntu@ubuntu:~$ e2fsck -f /dev/sdb1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sdb1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? 
That was the terminal response while in Try Ubuntu.. so that is a no!

---

### Post by dcbouchard on 2012-06-03
I figured out that "e2fsck -f /dev/sdb1" is not a command line for grub - I have no idea what to do next - I found this command line "sudo blkid -o list"  below is the result.  Please tell me what to do next in newb terms.  The response above has me baffled!!

ubuntu@ubuntu:~$ sudo blkid -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/loop1 ext3             (in use)       fa15a6ed-27fb-473c-a1a5-bff5a78a63bc
/dev/sda1  ext4             (not mounted)  7160b88f-9cb9-4620-bc72-c155bc3f75a3
/dev/sda5  swap             <swap>         a0381194-28f7-4e91-b7ac-42f7c6fb86de
/dev/sdb1  vfat             /cdrom         7AE8-FA70

---

### Post by pqwoerituytrueiwoq on 2012-06-03
> **dcbouchard said:**
> ```
/dev/loop0 squashfs         /rofs          
/dev/loop1 ext3             (in use)       fa15a6ed-27fb-473c-a1a5-bff5a78a63bc
/dev/**sda1  ext4**            ** (not mounted)**  7160b88f-9cb9-4620-bc72-c155bc3f75a3
/dev/sda5  swap             <swap>         a0381194-28f7-4e91-b7ac-42f7c6fb86de
/dev/sdb1  vfat             /cdrom         7AE8-FA70
```     
run this in a terminal
```
e2fsck -f /dev/sda1
```

---

### Post by dcbouchard on 2012-06-03
ubuntu@ubuntu:~$ e2fsck -f /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$

used "sudo" 

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: recovering journal
Error reading block 38329795 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? 

yes or no?
using "y" to everything.. we'll see what happens... lol

after a lot of "y"s this was result:
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 239792/19275776 files (0.2% non-contiguous), 2695417/77096448 blocks
ubuntu@ubuntu:~$ 

I will now remove usb stick and restart computer... hope this works!

---

### Post by dcbouchard on 2012-06-03
Thank you, thank you, thank you!!! I am back into my own profile... took a bit of time today to wait it out to find the "quick solution"... hopefully this helps other uber newbs like me!!!

---

