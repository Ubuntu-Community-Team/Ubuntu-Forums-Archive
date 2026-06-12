---
title: "Encrypted drive update issues"
date: 2016-08-11
forum: New to Ubuntu
---

### Post by jaydoe. on 2016-08-11
sorry, for writing here, i can't start a new thread... I will be thankful if some mod will transfer this

First of all, I'll state that I'm a newbie, but I feel like I did my  best and tried everything I found online before writing here.
  I started using ubuntu 16.04 while ago, I liked it, but it started to  crash all the time - before I read logs or did anything I assumed I  should update+upgrade, but in the middle of upgrading it crashed again -  I had to do cold reboot, after that I saw >grub rescue mode. 
  Tried to set right prefix for my partition, did so, but from >grub  rescue I couldn't manage to get insmod normal to work. All it said was  "normal.mod" not found.
  After that I booted ubuntu live from USB, connected to internet and  downloaded boot repair - Did run it (recommended mode), everything went  fine and software told me to reboot - but it didn't help or solve my  problem, still was at >grub rescue. Link to bootrepair log -> [http://paste2.org/6KtZyLLZ](http://paste2.org/6KtZyLLZ)
  Next I tried to mount the partition with ubuntu installed from  terminal, but after typing /sudo mount/dev/sda5 I'm getting: "mount:  unknown filesystem type 'crypto_LUKS'. Then I tried to mount encrypted  volume from command line and im getting other notification:     Error unlocking /dev/sda5:       GDBus.Error:org.freedesktop.UDisks2.Error.Failed: Device /dev/sda5 is  already unlocked as /dev/dm-0
  As I said, I'm a newbie and on one side of this I like digging and  learning while trying to figure it out, but on other side... I got  really valuable things on that PC, I got backup, but not up to date and I  lost few weeks of work.  Thanks in advance for any kind of help with this

---

### Post by oldfred on 2016-08-11
Moved.

I do not know encryption nor LVM.

Did you really need encryption? 
The use of LVM is required with full drive encryption, but that is a more advanced logical partition overlay over the standard physical partitions. Better for those a bit more knowledgeable on Linux.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

And errors or corruption on encrypted drives can be a lot more difficult to repair or becuase ot the encryption not possible to fix. Or very good regular backups is required.
 

    With LVM you mount the LVM, not the physical partition like /dev/sda5.

While this discusses resizing, all the first set of commands, are mounting an LVM install.
And it looks like Boot-Repair tried to run a fsck, but could not. You might get it to work if you manually mount & unencrypt first?
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by boxcorner on 2016-08-11
I too have had difficulty posting. I hope someone will be able to help you soon. I imagine your post is more likely to be seen if it can be transferred to a new thread. Try sending a private message to oldfred who has been helping me.

---

### Post by QIII on 2016-08-11
Rather than PMing a particular Staff Member, use the Report Post button to ask the Staff to move the thread.

That will make sure that all Staff who are currently available will see it.  If you PM a particular Staff member, you may have to wait until they are around.  Since we are all volunteers and spend time here as we have it to spend, your wait may be very long.

This also leaves a record in case questions arise about your thread in the future.

Cheers!

---

### Post by jaydoe. on 2016-08-11
> **oldfred said:**
> 
    With LVM you mount the LVM, not the physical partition like /dev/sda5.

While this discusses resizing, all the first set of commands, are mounting an LVM install.
And it looks like Boot-Repair tried to run a fsck, but could not. You might get it to work if you manually mount & unencrypt first?
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

@oldfred 
Thanks! Actually Boot-Repair worked after I manually mounted and unecrypted. 
I rebooted and now I'm out of >grub rescue, but I'm stack at >grub. I tried to select right partition to load kernel, but I guess because it's encrypted it causing me some extra stuff to do and I have no idea what next.

---

### Post by oldfred on 2016-08-11
Actually grub> is worse than grub rescue> 

But I know so little about LVM.
Have you tried the commands shown in link?

You just need to run commands thru:
> You can now manage your encrypted partitions, mount them, copy them, or perform maintenance (fsck, backup, resize).

And then run fsck, but with LVM partitions, I do not know details on running it.

---

### Post by jaydoe. on 2016-08-11
I didn't know it's so uncommon to use full disc encryption by default. And I had no idea it causes so much troubles in that scenario. I'm so lost right now, anyway:
I did run those commands, it worked, I get to the part where I run fsck:

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux 2.27.1

and that's it, nothing happens at all.

Tried this:
Scan all disks for partiitions: 

 
[LIST]
[*]lvm [pvscan]("http://linux.about.com/library/cmd/blcmdl8_pvscan.htm") 
[/LIST]
 Scan all disks for volume groups and build /etc/lvmtab and /etc/lvmtab.d/* which are the database for all other lvm commands:

 
[LIST]
[*]lvm [vgscan]("http://linux.about.com/library/cmd/blcmdl8_vgscan.htm") 
[/LIST]
 Change attributes of a logical volume

 
[LIST]
[*]lvm [lvchange]("http://linux.about.com/library/cmd/blcmdl8_lvchange.htm") -ay VolGroup00 
[/LIST]
 Scan all disks for logical volumes

 
[LIST]
[*]lvm [lvscan]("http://linux.about.com/library/cmd/blcmdl8_lvscan.htm") 
[/LIST]
 Then I was able to run fsck as follows

 fsck -f /dev/VolGroup00/LogVol00
But I'm lost at changing attributes of a logical volume. What I should type there in place of VolGroup00? 

```

ubuntu@ubuntu:~$ sudo lvm pvscan
  PV /dev/mapper/crypt1   VG ubuntu-vg       lvm2 [297.61 GiB / 0    free]
  Total: 1 [297.61 GiB] / in use: 1 [297.61 GiB] / in no VG: 0 [0   ]
ubuntu@ubuntu:~$ sudo lvm vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
ubuntu@ubuntu:~$ sudo lvm lvchange -ay VolGroup00
  Volume group "VolGroup00" not found
  Cannot process volume group VolGroup00
ubuntu@ubuntu:~$ sudo lvm lvscan
  ACTIVE            '/dev/ubuntu-vg/root' [293.81 GiB] inherit
  ACTIVE            '/dev/ubuntu-vg/swap_1' [3.80 GiB] inherit

```

Ok figured out what should be there instead of volgroup00 , then I run command 
 fsck -f /dev/VolGroup00/root
And i'm getting this as outcome, nothing else:
fsck from util-linux 2.27.1

I feel like blind man trying to find way to his home without his stick and after heavy drugs.


Edit2:
Managed to run it sudo fsck -nf /dev/ubuntu-vg/root
```
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/ubuntu--vg-root: 250926/19259392 files (0.4% non-contiguous), 12891951/77020160 blocks
```
Not quite sure what does it mean, if it found any errors or what?

EDIT3:
Somehow managed in grub prompt to figure out how to load kernel and get to the point of /boot working
this worked for me
```
insmod lvm
set root=(hd0,1)
linux /vmlinux-xx-xxxx-xx
initrd /initrd.xxxx-xxx-xxx
boot

```

After that stuff seems to load, plenty of green "OK'S", and it stops to tell me that I can try again to boot default by writing default or I can write some other **** to get some kind of report.

At this point I just want to get data back and I'm willing to pay if anyone can help me

---

### Post by oldfred on 2016-08-11
I believe your root is this, again, you have to think of the logical partitions as what you deal with not the physical partition. 
/dev/ubuntu-vg/root

---

### Post by HermanAB on 2016-08-12
Well, a computer should not crash.  A Linux server can run for many years without ever crashing or restarting.  A Linux laptop can run for many years without ever restarting - just suspend when the lid is closed.

So if your machine is crashing, then there is something really wrong with it and you need to fix the hardware first, before your try to fix the software, otherwise you will go nowhere fast.

That being said, when an encrypted disk becomes corrupted, you usually lose all the information on it.  Backups are important.

---

### Post by jaydoe. on 2016-08-12
At this point I don't really care about linux crashing or not - it happend and I can't do nothing about it, all I want is to get data back. 
I'm stuck at emergency mode for now. I can view log by typing journactl -xb, reboot or keep pressing control + D to continue, but nothing happens after that, only fast check to 100%... I can also press "enter" for "maintance" but have no idea what to type there and can't find nothing on web about how to get out of this loop. Is this dead end as Herman says and I can't do anything about it?
Ah, after I reboot I get back to >grub again.

---

### Post by HermanAB on 2016-08-12
It would be best to get a properly working reliable computer and use that to try to recover your data.

Otherwise, try running an install CD/USB stick and see what it makes of the disk drive.

---

### Post by jaydoe. on 2016-08-12
My other question is, if I can mount LVM volume while I'm on live usb, can I somehow get files back? Can I get access to the files somehow?

---

### Post by oldfred on 2016-08-12
If you can mount & unencrypt from live installer, you should be able to then copy files.
But if still corruption on partition that would have to be resolved first as you may not be able to mount it.

---

### Post by jaydoe. on 2016-08-12
So I'm trying to access data to backup it, but seems like I won't be able to do that as well...

first, tried sudo -H nautilus to browse encrypted files, but after I open home folder I see "Readme.txt" and "Access-your-private-data-desktop". When I click it, nothing happens.
Tried from terminal:
```
ubuntu@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
find: &#8216;/run/user/999/gvfs&#8217;: Permission denied
find: File system loop detected; &#8216;/sys/kernel/debug/pinctrl&#8217; is part of the same file system loop as &#8216;/sys/kernel/debug&#8217;.
ubuntu@ubuntu:~$  ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
ubuntu@ubuntu:~$ a
```

---

### Post by jaydoe. on 2016-08-12
Ok, I've attempted to run boot-repair once again (from lack of other ideas), seems it worked, reinstalled and purged grub (by accident i did it on all available drives, so i screwed my live usb installation, meh), but after reboot insmod normal worked and it loaded to normal grub screen where I have options to choose to boot Ubuntu / Ubuntu recovery / Ubuntu startup. No matter what option I choose, the Busybox prompt loads and initriamfs. Tried to mount -t ntfs-3g /dev/sda1 /root -o force, but it says it can't be found in fstab...

No clue what to do next, I really appreciate you guys trying to help the newbie out...e

---

### Post by oldfred on 2016-08-12
If you have LVM, you have no NTFS to mount.
And sda1 is normally your /boot which is not encrypted. If UEFI it may be the ESP which then is FAT32 and sda2 if /boot.
And then either sda3 or sda5 is the LVM logical partitions with at least the default of / & swap, but may have others also.

Your Boot-Repair summary showed sda5 as the LUKS logical LVM partition.
And you showed these logical:
```
ubuntu@ubuntu:~$ sudo lvm lvscan
  ACTIVE            '/dev/ubuntu-vg/root' [293.81 GiB] inherit
  ACTIVE            '/dev/ubuntu-vg/swap_1' [3.80 GiB] inherit
```

My normal install logic from many years ago even with Windows is to separate system from data. Windows makes that difficult, but with Ubuntu I use / as 25GB and have /mnt/data for all data. For newer users I suggest separate /home as that can easily be set up during install where data partition(s) have to be manually added and ownership & permissions set & added to fstab for automounting.

---

### Post by jaydoe. on 2016-08-12
Sorry for making you stating the obvious stuff, I'm feeling ashamed for asking those questions, but I'm desperate to get data back. Hope you understand.
Following what you wrote, I'm trying other commands in busybox trompt, result:

mount -t FAT32 /dev/sda5 /root -o force 
mounting /dev/sda5 on /root failed: No such device
same with sda2
when just mount -t /dev/sda2(or5) /root -o force
can't find /root in etc/fstab
Combination with 
mount -t FAT32 /dev/ubuntu-vg/root doesn't work as well. 

I never worked with linux before, read great things about ubuntu and I without knowledge how stuff works I'm learning the hard way. Not like I'm willing to go back to windows, but surely my next linux installations will be much more aware.
Should I keep trying in busybox, or maybe I'll be able to do something from live installation and terminal?

---

### Post by oldfred on 2016-08-12
Your Linux partitions are ext4, not NTFS nor FAT32.

But if manually mounting you have to use the LVM partitions, not the physical partitions.
I have never used LVM so do not know details.

There is no /root (except as a hidden folder in / (root) used as /home by / when you use sudo.
You always see root as / in fstab and mount.

My mount but this is not LVM:
```
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)

```
My fstab:
```
# / was on /dev/sda6 during installation
UUID=255a2800-b871-4fdf-a809-16987e64b8b3 /               ext4    errors=remount-ro 0       1

```

Your original Summary report did not show fstab as it could not mount / , as you said you had not unencrypted it so it could then show entries from /. 
You /boot had the grub entries, since /boot is not encrypted:
> linux	/vmlinuz-4.4.0-22-generic root=[COLOR=#ff0000]/dev/mapper/ubuntu--vg-root[/COLOR] ro

Again where I normally have / and mount of partitions, usually by UUID, you have LVM and / is mounted to the mapper, not a physical partition.

---

### Post by jaydoe. on 2016-08-16
So I've tried everything in initramfs prompt, and I'm getting: 
LVM cant boot - alert /dev/mapper/ubuntu--vg-root does not exist, dropping to shell
after typing in initramfs prompt this path:
mount -t ext4 /dev/mapper/ubuntu--vg-root
it just tells me it can't be found or mounted
I read somewhere LVM is not supported by initramfs, I have no clue what else here can be done. Maybe I should start a new thread with current state and problem and someone who had similar problem could help me out? I couldn't find nothing in documentation or online. Found some similar threads, but nothing solved or from 2010. Whole thing feels like challange after challange, managed to get out grub rescue to regular grub, then somehow to the point it boots and for a while i thought it's fixed just to show me another prompt after regular ubuntu loading screen, this time with initramfs. 
I can mount LVM from live usb to get to the fstab, which is:
```
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
```
but I can't get access to the files which I would like to backup.

---

### Post by oldfred on 2016-08-16
Your fstab is in /, so then if you can see it, you should be able to see all your files if unencrypted and mounted in /home.
If that is your entire fstab, then it is missing the mount of /boot. It only shows the comment that it was sda1.

---

### Post by jaydoe. on 2016-08-16
It's not entire fstab, I just copied 2 lines of it as you did. 
I'm able to r/w fstab, but when I'm trying to open home directory and my username directory inside it tells me I don't have permission viewing contest of it. 
Did that:
encryption:
```
ubuntu@ubuntu:~$ sudo apt-get install cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cryptsetup is already the newest version (2:1.6.6-5ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 76 not upgraded.
ubuntu@ubuntu:~$ sudo modprobe dm-crypt
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 pleasework
Enter passphrase for /dev/sda5: 
Cannot use device /dev/sda5 which is in use (already mapped or mounted).
```
lvm:
```
ubuntu@ubuntu:~$ sudo apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version (2.02.133-1ubuntu10).
0 upgraded, 0 newly installed, 0 to remove and 76 not upgraded.
ubuntu@ubuntu:~$ sudo modprobe dm-mod
ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -a y ubuntu-vg
  2 logical volume(s) in volume group "ubuntu-vg" now active
ubuntu@ubuntu:~$ sudo lvscan
  ACTIVE            '/dev/ubuntu-vg/root' [293.81 GiB] inherit
  ACTIVE            '/dev/ubuntu-vg/swap_1' [3.80 GiB] inherit
  
```
Then mounted:
```
ubuntu@ubuntu:~$ sudo mkdir /media/root; sudo mkdir /media/home
ubuntu@ubuntu:~$ sudo mount /dev/ubuntu-vg/root /media/root 
```
And i'm still can't get access to files at all. Am I missing something?

---

### Post by oldfred on 2016-08-16
If you have mounted sda5 unencrypted, then is the issue that you cannot mount it again to unencrypt it?

Never used encryption nor LVM, so do not know details.

But you did not have a separate LVM partition for /home, so you do not separately mount it. You only have / & swap. 
So then /home is just another folder under /. 
When you looked at fstab you should have been at /etc/fstab where /etc is a folder off / just like /home is.

---

### Post by jaydoe. on 2016-08-16
I can just press on the encrypted volume in my dock on ubuntu and it ask for a password to unencrytp, I can type that password and it opens window of volume. I can see all folders and I can access etc/fstab for example, but folder "root" or folder MyUsername in /home has small "x" on corner of icon and when I'm trying to open it it says: "This location could not be displayed. You don't have permission to view the contents of "root" or "MyUsername".
When I do this from terminal, as I said in previous post, installing cryptsetup and enabling modules, result is the same.

---

### Post by oldfred on 2016-08-17
I just installed Yakkety to a partition on sdb. While in installer, I browsed my /home inside my / which is on sda without issue. 
So may still be related to LVM & encryption?

There may be issues where live installer is user 999 where actual install uses 1000, so then you have to use sudo.
And new installs change mounts of the ESP - efi system partition to umask=0077     in fstab, which is no permissions at all. But normal partition use defaults. And access to folder root in / normally cannot be accessed, so that is normal.
And corrupted partitions may not mount but you may be able to force mount in ro read only mode, but usually need fsck to repair.

---

### Post by jaydoe. on 2016-08-17
Should I install 16.10 too then? You think I'll be able to browse /home from installer? 
I was already trying to open /home with sudo though, I tried to change permissions with chmod too. 
Maybe I shouldn't focus on trying to decrypt /home and backup my files, but on trying to repair and get out from initramfs?
Should I run fsck? 
After I mount the encrypted partition and run
```
sudo ecryptfs-recover-private
```
im getting this
```
INFO: Searching for encrypted private directories (this might take a while)...
find: &#8216;/run/user/999/gvfs&#8217;: Permission denied
find: File system loop detected; &#8216;/sys/kernel/debug/pinctrl&#8217; is part of the same file system loop as &#8216;/sys/kernel/debug&#8217;.
```

after running fsck:
```
sudo fsck -f /dev/ubuntu-vg/root
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/ubuntu--vg-root: 283236/19259392 files (0.4% non-contiguous), 12994516/77020160 blocks

```

---

### Post by oldfred on 2016-08-17
I think you need to resolve the error on the system loop first.
Edit similar issues, may have some hints on fixes:
[http://askubuntu.com/questions/699056/how-can-i-access-my-encrypted-hard-drive-on-another-pc](http://askubuntu.com/questions/699056/how-can-i-access-my-encrypted-hard-drive-on-another-pc)
[http://askubuntu.com/questions/694947/encryption-help](http://askubuntu.com/questions/694947/encryption-help)

I also have this in my notes on -f

 Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 

When I look at man fsck I do not see -f
But man e2fsck:
    -f     Force checking even if the file system seems clean.

---

### Post by jaydoe. on 2016-08-17
How I can resolve system loop when I can't do nothing at all in initramfs? I can just watch the prompt and nothing works.

Did e2fsck -f, result is similar as previously:
```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/ubuntu-vg/root
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/ubuntu-vg/root: 283236/19259392 files (0.4% non-contiguous), 12994516/77020160 blocks

```

Both links I saw already and I've tried everything suggested there

pvs
```
ubuntu@ubuntu:~$ sudo pvs
  PV                                                    VG        Fmt  Attr PSize   PFree
  /dev/mapper/luks-c3bc6b58-6571-475c-9c39-1fa274cb2121 ubuntu-vg lvm2 a--  297.61g    0 
```
lvdisplay 
```
ubuntu@ubuntu:~$ sudo lvdisplay /dev/ubuntu-vg
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID               
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-04-24 00:36:21 +0000
  LV Status              available
  # open                 1
  LV Size                293.81 GiB
  Current LE             75215
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-04-24 05:36:21 +0500
  LV Status              available
  # open                 0
  LV Size                3.80 GiB
  Current LE             973
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
```

I can mount from terminal to /mnt
```
$ mount /dev/ubuntu/home /mnt/disk
```
But I still can't access /home or /root in /mnt.

Result of ls -l /mnt after:

```
ubuntu@ubuntu:~$ ls -l /mnt
total 124
drwxr-xr-x   2 root root  4096 Aug 11 01:11 bin
drwxr-xr-x   3 root root  4096 Aug 11 18:01 boot
drwxr-xr-x   3 root root  4096 Aug 12 16:17 BootInfo
drwxr-xr-x   4 root root  4096 Aug 12 16:02 boot-sav
drwxr-xr-x   2 root root  4096 Apr 24 00:41 cdrom
drwxr-xr-x   5 root root  4096 Apr 20 22:15 dev
drwxr-xr-x 142 root root 12288 Aug 12 16:17 etc
drwxr-xr-x   4 root root  4096 Apr 24 00:41 home
lrwxrwxrwx   1 root root    32 Aug 12 16:14 initrd.img -> boot/initrd.img-4.4.0-34-generic
lrwxrwxrwx   1 root root    32 May 13 16:04 initrd.img.old -> boot/initrd.img-4.4.0-22-generic
drwxr-xr-x  24 root root  4096 Aug 12 16:04 lib
drwxr-xr-x   2 root root  4096 Apr 20 22:07 lib64
drwx------   2 root root 16384 Apr 24 00:36 lost+found
drwxr-xr-x   5 root root  4096 Aug 11 01:00 media
drwxrwxrwx   3 root root  4096 Apr 24 04:15 mnt
drwxr-xr-x   3 root root  4096 Apr 24 02:53 opt
drwxr-xr-x   2 root root  4096 Apr 12 20:14 proc
drwx------   8 root root  4096 Apr 24 05:21 root
drwxr-xr-x  11 root root  4096 Aug 11 17:58 run
drwxr-xr-x   2 root root 12288 Aug 12 16:04 sbin
drwxr-xr-x   2 root root  4096 Apr 19 14:31 snap
drwxr-xr-x   2 root root  4096 Apr 20 22:07 srv
drwxr-xr-x   2 root root  4096 Feb  5  2016 sys
drwxrwxrwt   7 root root  4096 Aug 12 16:17 tmp
drwxr-xr-x  11 root root  4096 Apr 20 22:13 usr
drwxr-xr-x  14 root root  4096 Apr 20 22:19 var
lrwxrwxrwx   1 root root    29 Aug 12 16:14 vmlinuz -> boot/vmlinuz-4.4.0-34-generic
lrwxrwxrwx   1 root root    29 May 13 16:04 vmlinuz.old -> boot/vmlinuz-4.4.0-22-generic
```

ecryptfs-recover-private
```
ubuntu@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/999/gvfs’: Permission denied
find: File system loop detected; ‘/sys/kernel/debug/pinctrl’ is part of the same file system loop as ‘/sys/kernel/debug’.
```
And can't do nothing about it...

---

### Post by jaydoe. on 2016-08-17
So, update on initramfs:
Read somewhere that people were able to boot after typing vgchange -a y in initramfs, 
in my case after I typed that:
```
initramfs: lvm vgscan
/run/lvm/lvmetad.socket: connect failed. no such file or directory
```

what it says before initramfs prompt opens:
```
lvmetad is not active yet, using direct activation during sysinit
```

---

### Post by oldfred on 2016-08-17
If at the post above where you did the ls, can you drill down deeper?
ls -l /mnt
Try
ls -l /mnt/home/$USER # or your user name in system.

I am getting not authorized error (Forum has issues) on PM. But no thanks.

---

### Post by jaydoe. on 2016-08-18
```
ubuntu@ubuntu:~$ ls -l /mnt/home/my_username
ls: cannot open directory '/mnt/home/my_username': Permission denied
```

Added in grub "nomodeset" after "quiet splash", as I read somewhere it did the job for some people with similar error during booting as mine (lvmetad is not active yet, using direct activation during sysinit), didn't help though. I also read some people can access login from initramfs prompt by pressing alt+f1/f2, also doesn't work for me.

---

### Post by oldfred on 2016-08-18
Did you actually use my_username? Unless that is your actual name you use to log in with, it is wrong. 

When I directly mount in my working install to /mnt it wipes out my other mounts in mnt, so I added a /temp:

552  sudo blkid
  553  mkdir /mnt/temp
  554  sudo mkdir /mnt/temp
  555  sudo mount /dev/sda3 /mnt/temp
  556  cd /mnt/temp
  557  ls
  558  cd home
  559  ls
  560  cd fred
  561  ls

Numbers are because I copied from my history, so you would not use those. And your ls -l tells more, I just wanted a quick example. sda3 is my old 14.04 install and I mounted it in my 16.04 install.

---

### Post by jaydoe. on 2016-08-18
Nah, I used my actual username, not "My_username" :)

Added /temp, same outcome though, no permission:

```

ubuntu@ubuntu:~$ blkid
/dev/sda1: UUID="0cdf7e0e-656b-4fb8-9598-7ad3083806a6" TYPE="ext2" PTTYPE="dos" PARTUUID="c0ef39a8-01"
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="AC33-206E" TYPE="vfat" PARTUUID="0673e85d-01"
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="0cdf7e0e-656b-4fb8-9598-7ad3083806a6" TYPE="ext2" PTTYPE="dos" PARTUUID="c0ef39a8-01"
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="AC33-206E" TYPE="vfat" PARTUUID="0673e85d-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="c3bc6b58-6571-475c-9c39-1fa274cb2479" TYPE="crypto_LUKS" PARTUUID="c0ef39a8-05"
/dev/mapper/luks-c3bc6b58-6571-475c-9c39-1fa274cb2479: UUID="kpc4v5-z7w3-q1tf-HV1n-05xd-rCz9-Csl1yM" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="2c4a16b8-28a2-4e5a-a4fc-67dff7debd89" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="6ac8aa51-ebee-491b-874d-4a6bb0e6de28" TYPE="swap"

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/ubuntu-vg/root /mnt/temp
ubuntu@ubuntu:~$ cd /mnt/temp
ubuntu@ubuntu:/mnt/temp$ ls

bin       cdrom  initrd.img      lost+found  proc  snap  usr
boot      dev    initrd.img.old  media       root  srv   var
BootInfo  etc    lib             mnt         run   sys   vmlinuz
boot-sav  home   lib64           opt         sbin  tmp   vmlinuz.old

ubuntu@ubuntu:/mnt/temp$ cd home
ubuntu@ubuntu:/mnt/temp/home$ ls
My_username
ubuntu@ubuntu:/mnt/temp/home$ cd My_username
bash: cd: My_username: Permission denied
```


I read that turning off this command could help, but how do I apply this to work after reboot? I have to update kernel somehow with that?
I edited with nautilus this file:

mnt/temp/etc/lvm/lvm.conf 

Turned off "use_lvmetad" which was on "1"

```
etc/lvm/lvm.conf set:  use_lvmetad = 0
```

```
ubuntu@ubuntu:~$ sudo systemctl status lvm2-lvmetad
&#9679; lvm2-lvmetad.service - LVM2 metadata daemon
   Loaded: loaded (/lib/systemd/system/lvm2-lvmetad.service; enabled; vendor pre
   Active: active (running) since Thu 2016-08-18 15:50:30 UTC; 58min ago
     Docs: man:lvmetad(8)
 Main PID: 2150 (lvmetad)
   CGroup: /system.slice/lvm2-lvmetad.service
           &#9492;&#9472;2150 /sbin/lvmetad -f

Aug 18 16:13:04 ubuntu systemd[1]: Started LVM2 metadata daemon.
lines 1-9/9 (END)
```


Just to keep it clear, same error for some people was caused by some kind of graphics errors, I assumed if my system crashed while it was updating it might be the cause, but seems like it's not the case - in grub I added "nomodeset", booted with really bad quality to the same point - initramfs and same error:  lvmetad is not active yet, using direct activation during sysinit.


Edit:
Now I wonder if my fstab is all good. I'm not sure, but when I was trying to get out >grub rescue I might add some suggested line there. Does it look like a regular fstab?

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
#UUID=0cdf7e0e-656b-4fb8-9598-7ad3083806a6 /boot           ext2    defaults        0       2
#/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
UUID=0cdf7e0e-656b-4fb8-9598-7ad3083806a6    /boot    ext2    defaults    0    2
```

---

### Post by oldfred on 2016-08-18
You normally would be mounting swap, but not mounting it should not be related to any permission errors.
But again I do not know details of LVM?

change this to the ls -l command and try with sudo:
ubuntu@ubuntu:/mnt/temp/home$ ls

Now I use same user in all my installs, so they all are fred.

When I run this I see all the folders and a few files I have in /home/fred in my 14.04 install.
fred@Asusz97:~$ ls -l /mnt/temp/home/fred

Also live installer is probably user 999 from my 16.04 install, I am the default user 1000. I did not check when booted in live installer to verify new systems are still that way. Again LVM may be different also.
fred@Asusz97:~$ cat /etc/passwd | grep fred
fred:x:1000:1000:Fred,,,:/home/fred:/bin/bash



fred@Asusz97:~$ ls -l /mnt/temp/home
total 4
drwxrwxr-x 37 fred fred 4096 Apr 29 14:26 fred

---

### Post by jaydoe.. on 2016-08-18
So, couldn't login to my forum account, each time after login attempt I had "permission error"...

anyway:
```

ubuntu@ubuntu:/mnt/temp/home$ sudo ls -l /mnt/temp/home/myusername
total 0
lrwxrwxrwx 1 1000 1000 56 Apr 24 00:41 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 1000 1000 52 Apr 24 00:41 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

```
Basically I was at this point already where those 2 files appear, using nautilus trying to browse /home I see those two files. encrypts-mount-private doesn't work, encrypfs-recover-private also. Even if it worked, I don't have a backup of encrypfs passphrase which apparently is something different than regular login passphrase. Meaning I should give up trying to get access to files this way, my only hope is to somehow fix: error on booting that kicks me out to initramfs prompt... "lvmetad is not active yet, using direct activation during sysinit."

---

### Post by jaydoe.. on 2016-08-18
Don't know if that matters or helps, but from lack of other ideas downloaded "bootinfoscript" as it helps with troubleshooting:
[http://pastebin.ubuntu.com/23068808/](http://pastebin.ubuntu.com/23068808/)

This is the warning I received after updating initramfs:
```
root@ubuntu:/home/ubuntu# mkdir /mnt/system
root@ubuntu:/home/ubuntu# mount /dev/mapper/ubuntu--vg-root /mnt/system
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt/system/boot 
root@ubuntu:/home/ubuntu# for i in /dev/pts /dev/proc /sys; do mount -B $i /mnt/system$i; done
mount: mount point /mnt/system/dev/proc does not exist
root@ubuntu:/home/ubuntu# for i in /dev/pts /dev/proc /sys; do mount -B $i /mnt/system$i; done
mount: mount point /mnt/system/dev/proc does not exist
root@ubuntu:/home/ubuntu# for i in /dev/pts /dev /proc /sys; do mount -B $i /mnt/system$i; done
root@ubuntu:/home/ubuntu# chroot /mnt/system
root@ubuntu:/# update-initramfs -k all -c
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-c3bc6b58-6571-475c-9c39-1fa274cb2479 - 
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-c3bc6b58-6571-475c-9c39-1fa274cb2479 - 
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-c3bc6b58-6571-475c-9c39-1fa274cb2479 - 

```

Following this thread: [https://ubuntuforums.org/showthread.php?t=2264947](https://ubuntuforums.org/showthread.php?t=2264947)
Last response is:
> 
Along with an academic I roped in we managed to fix the problem.

To answer your Question:
update-initramfs did give errors but only on some Kernels but since we  only wanted to boot on some of the later ones we first thought it's not  the issue (which it was).

In a nutshell this Academic writing board sums it up:
[https://www.dropbox.com/s/4x1nqsvlhg...oting.JPG?dl=0]("https://www.dropbox.com/s/4x1nqsvlhg01yqs/initramfs-issue-booting.JPG?dl=0")

so after installing lvm on live disk and chrooting,
then had to remove 3.11.10-26,24,10 etc

the in teh chrooted environment 
dpkg -i lvm2*.deb - > the deb file copied from the LiveDisk lvm install caches area previously.

Thanks for the help though.
Could someone explain what does he mean by "then had to remove 3.11.10-26,24,10 etc(...)" ? Does it mean he removed all kernels?

---

### Post by oldfred on 2016-08-18
He may have had incorrect or old kernels and only wanted newest.

See this:
man update-initramfs
System normally runs that as part of new kernel or grub to recreate a new boot image. That integrates all drivers into kernel image for initial booting. In your case I would expect it includes the lvm2 driver & whatever the encryption program is.

And I have no idea what settings are correct in  /etc/crypttab, but some of the previous posts on encryption may have details.

Edit, this may have more info:
[https://wiki.archlinux.org/index.php/Dm-crypt/System_configuration](https://wiki.archlinux.org/index.php/Dm-crypt/System_configuration)

---

