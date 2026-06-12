---
title: "How to reclaim space from other old ubuntu installation on the same box?"
date: 2023-11-15
forum: New to Ubuntu
---

### Post by mvelanka on 2023-11-15
I am/was using Ubuntu 18.04 for last 4-5 years without problem. Recently my box had an issue and it had to be powered down. After powered up again, it was not able to access Ethernet at all. I tried a couple of ways but did not go far. So I decided to install another Ubuntu (the latest 23.04). While installing it installed side by side with the old 18.04 Ubuntu. It comes up well and no issues with internet etc. However it has a very limited space allocated. The older install had almost 2 TB available. (only about 20% was used so far)

So my question.

How can I work with this recent Ubuntu? I want to 'reclaim' the space that is not used by old Ubuntu. (And if that works,  I will remove many unwanted files once the new one starts working well. ... So even more space available!!)

That is my wish.

Can I achieve it?  How if yes?.
Please guide me step by step. I will patiently follow all the steps and give feedback.

Thanks in advance
-Mahesh

---

### Post by Rubi1200 on 2023-11-16
Hi and welcome to the forums -:)

Boot into whichever Ubuntu install is currently working and then run these commands separately and post the output here.

When replying, please click on Go Advanced >> paste the output >> highlight the text and then click on the # icon to wrap with code tags. It makes it much easier for us to analyze the results.

```
sudo fdisk -l

lsblk -e 7 -o name,size,type,fstype,mountpoint

df -hT -x squashfs -x tmpfs -x devtmpfs

```

Thanks.

---

### Post by Dennis N on 2023-11-16
> So I decided to install another Ubuntu (the latest 23.04)
Before you start, consider installing Ubuntu 23.10. 23.04 is not the latest; in fact it will be end-of-life in late January 2024 and no longer supported.

---

### Post by mvelanka on 2023-11-16
Hi Rubi
Thanks for taking time to guide me.
Here are the commands and responses:

```
sudo fdisk -l
```
```
Disk /dev/loop0: 219 MiB, 229638144 bytes, 448512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.45 MiB, 58130432 bytes, 113536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 50.98 MiB, 53432320 bytes, 104360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 32.3 MiB, 33865728 bytes, 66144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 65.1 MiB, 68259840 bytes, 133320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 55.68 MiB, 58363904 bytes, 113992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 40.88 MiB, 42840064 bytes, 83672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 73.92 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: TOSHIBA DT01ACA2
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C1DA5DA4-D79D-4084-AECD-E72C64E62B6F

Device     Start        End    Sectors  Size Type
/dev/sda1   2048       4095       2048    1M Linux filesystem
/dev/sda2   4096 3907026943 3907022848  1.8T Linux filesystem


Disk /dev/sdb: 119.25 GiB, 128035676160 bytes, 250069680 sectors
Disk model: SK hynix SC311 S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 8FA24122-ED65-445E-9076-AF10A91C62A0

Device         Start       End   Sectors  Size Type
/dev/sdb1       2048   1333247   1331200  650M EFI System
/dev/sdb2    1333248   1595391    262144  128M Microsoft reserved
/dev/sdb3    1595392 167861293 166265902 79.3G Microsoft basic data
/dev/sdb4  222201856 223135743    933888  456M Windows recovery environment
/dev/sdb5  223135744 247814143  24678400 11.8G Windows recovery environment
/dev/sdb6  247816192 250048511   2232320  1.1G Windows recovery environment
/dev/sdb7  167862272 167864319      2048    1M BIOS boot
/dev/sdb8  167864320 168914943   1050624  513M Microsoft basic data
/dev/sdb9  168914944 222201855  53286912 25.4G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/loop8: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 218.4 MiB, 228999168 bytes, 447264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 91.7 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 496.10 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
```
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda      1.8T disk
&#9500;&#9472;sda1     1M part
&#9492;&#9472;sda2   1.8T part ext4   /media/velama02/871028de-6355-11e8-b061-8cec4b5daf0d
sdb    119.2G disk
&#9500;&#9472;sdb1   650M part vfat
&#9500;&#9472;sdb2   128M part
&#9500;&#9472;sdb3  79.3G part ntfs
&#9500;&#9472;sdb4   456M part ntfs
&#9500;&#9472;sdb5  11.8G part ntfs
&#9500;&#9472;sdb6   1.1G part ntfs
&#9500;&#9472;sdb7     1M part
&#9500;&#9472;sdb8   513M part vfat   /boot/efi
&#9492;&#9472;sdb9  25.4G part ext4   /
```
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb9      ext4   25G   17G  7.2G  70% /
/dev/sdb8      vfat  512M  4.0K  512M   1% /boot/efi
/dev/sda2      ext4  1.8T  375G  1.4T  22% /media/velama02/871028de-6355-11e8-b061-8cec4b5daf0d
```
HTH
Thanks
-Mahesh

---

### Post by mvelanka on 2023-11-16
Hi Dennis N.,
Actually I just checked the Ubuntu version:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal
```
I will now require to ask our system guys to look for the new Ubuntu. Till then I will continue with this one.

Sorry for not looking into this earlier and reporting incorrect version in the post.
Thanks for your support
-Mahesh

---

### Post by yancek on 2023-11-16
If you want to shrink what shows in your output as sda, you can boot to the new Ubuntu on sdb and use GParted.  It may not be installed but will be on the 'live' usb you used to install Ubuntu so you could also use that.  GParted should show how much space is used on that partition so shrink so it is a little larger than the used space or to whatever size you want.  If you are not familiar with GParted, the link below is to their online manual which gives detailed information.  It would be a good idea to read through the first part of the manual to familiarize yourself with the options.

  [https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by TheFu on 2023-11-16
a) thanks for the output. Save those commands with the options. They are extremely useful to get help around storage questions.
b) 23.04 isn't LTS and support for it ends in January, so having Ubuntu 20.04 **is** a better option from a support standpoint, assuming it is either a server or the main, Gnome-based, Ubuntu Desktop.  All other Desktop flavors of Ubuntu lost most of their support last May-ish.  It would be good to learn about support periods for your specific flavor and to upgrade to the next LTS before your current release drops support.  Upgrades of supported systems are much easier than non-supported versions.
c) 20.04 with either non-GUI Ubuntu Server or Gnome 4.x DE are supported for 5 yrs. Other flavors get 3 yrs, so support ended for Xubuntu, Lubuntu, Ubuntu-Mate, Kubuntu last spring.
d) Any new install that isn't a server really should be 22.04 and 22.04 server would also be an excellent choice.

Ok, to the meat of the issue:

```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb9      ext4   25G   17G  7.2G  70% /
/dev/sdb8      vfat  512M  4.0K  512M   1% /boot/efi
/dev/sda2      ext4  1.8T  375G  1.4T  22% /media/velama02/871028de-6355-11e8-b061-8cec4b5daf0d
```
There are many things that are possible. The choices are nearly infinite. That's good and that's bad, since you have some choices to make.

If I clean up this output to remove the junk and non-NTFS stuff, 
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda      1.8T disk
&#9500;&#9472;sda1     1M part
&#9492;&#9472;sda2   1.8T part ext4   /media/velama02/871028de-6355-11e8-b061-8cec4b5daf0d
sdb    119.2G disk
&#9500;&#9472;sdb1   650M part vfat
&#9500;&#9472;sdb8   513M part vfat   /boot/efi
&#9492;&#9472;sdb9  25.4G part ext4   /
```
What I see and make assumptions around is a new install on a 120G storage with the FAT32 EFI partition and a 25G / for whatever the new OS is, 20.04 is what you claim.
I also see a single, huge 1.8T ext4 partition that was setup in a not-so flexible way, which leads you do this issue.  It is smart to have a per partitions for different uses under Linux.  The most important extra partitions would be for /home and for some data that is shared between many different users.  With only 1 huge partition, your prior setup didn't follow those guidelines, unfortunately.  

Additionally,  /media/velama02/871028de-6355-11e8-b061-8cec4b5daf0d doesn't even have a partition LABEL, so the mount that happened automatically uses an ugly name.  You can use gparted to add a LABEL to that partition, and it will mount as  /media/velama02/{LABEL} next time. Or better, you could modify the fstab file and mount it somewhere specific to your needs, perhaps /home, after moving some of the data around a little to make it a bit cleaner.  

Since that "huge" storage device is only using about 400G of stuff, you have plenty of room to split it into multiple partitions and create a smarter disk layout.  However, the details for doing this are not noob-friendly.  Don't get me wrong, they aren't hard, just people uncomfortable with moving large amounts of data around tend to make mistakes and have data loss.  But if you are willing and don't need EXACT commands, then I'm happy to provide overview steps.
[LIST=1]
[*]
[*]Backup anything you don't want to lose. The backups needs to contain not just the files, but the owner, group, permissions, ACLs and xattrs for every single file.  Without those last parts, the backs are for ****.  Copying files to NTFS loses all but the file data, so it isn't a viable way to make a backup.
[*]Resize the 1.8TB file system and partition down to 400GB or so.  This should be relatively safe, but you'll want to validate using the backups that there wasn't any data loss after the resize. I'd probably use gparted for this.
[*]Create a new partition just for your HOME directories. Format it as ext4 and give it a LABEL of "home-01".  The goal would be to place everything from the old /home/ into it, retaining users, groups, permissions, ACLs, xattrs, then using a life-boot flash drive, I'd merge the 20.04 /home stuff with the older 18.04 /home, keeping only what you need. If you aren't too tied to the new /home, it doesn't have many critical new files, I'd just copy the 10 newest files to the older 18.04 /home version. Put the files in the same subdirectories.  Then I'd setup the new 20.04 /etc/fstab to mount to new "home" partition to /home.  The fstab line to do this is
```
LABEL=home-01   /home   ext4  defaults  0 1
```
if you want a little stronger security, make it 
```
LABEL=home-01   /home   ext4  defaults,nodev,nosuid 0 1
```
This step will make it so the 18.04 OS cannot be booted anymore.
[*] If you feel adventurous, you can create a 4.1G swap partition, add a LABEL, say swap-01, use mkswap to format it, then add that to your /etc/fsab too.  After you do this, you can delete the swapfile or prior swap partition.  Don't forget to remove that swap line from the fstab file.
```
LABEL=swap-01   none             swap sw 0 0
```
[*] If you still feel adventurous, you can create a /var partition and format it as ext4, give it a LABEL, say var-01, then add that to your  /etc/fsab too.  Sizing of /var is a personal thing. If you use lots of snap packages, you'll probably want 10-20G.  If you remove the snap subsystem, then it can be much smaller, say 4G.  After the file system is created, using a bootable Live Flash drive, you'll need to move the current /var over to the newly created one.  
```
LABEL=var-01   /var   ext4  defaults 0 1
```
[/LIST]

None of this is hard, but it does require keeping track of where a file system is currently mounted vs where it will be mounted when we are all done.  Especially under a Live-Boot flash drive environment, I like to have a system that uses "old" and "new" so I know which had the old data and where that data gets moved under "new" for each file system/partition. It is just accounting, but people get confused all the time with this.

In the old 1.8TB storage, now just 400G, will be the old 18.04 OS.  It has the old config files for the OS, which you can use as reference.  Really, those should be in the /etc/ area only, so you can probably delete the old area with /usr, /bin, /lib, directories. That will probably only reduce the storage about 20-40G, if that.  If it were me, I'd set a calendar reminder for 30-7 5 days to come back and delete those areas AFTER I've already completely moved to the new OS.

By using LABELs, we simplify the fstab mount lines.  We've created 3 partitions, 3 file systems, moved 2 old directory structures over to the new areas AND setup mounts for them under the 20.04 OS instance.  We haven't really touched the 20.04 24G OS partition, but we probably did remove all of /home, /var, and a swapfile under it, so it will be using less storage now.  My very minimal 20.04 install uses these sizes:
```
&#9492;&#9472;nvme0n1p4          part  LVM2_member 930.8G                               
  &#9500;&#9472;vg01-swap01      lvm   swap          4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01      lvm   ext4           35G   25.3G    21%                /
  &#9500;&#9472;vg01-var01       lvm   ext4           20G   15.2G    17%                /var
  &#9500;&#9472;vg01-tmp01       lvm   ext4            4G    3.3G    10% tmp01          /tmp
  &#9500;&#9472;vg01-home01      lvm   ext4           20G   12.9G    30% home01         /home

```
So after you clean up some things, we can take a look at dealing with some of the NTFS stuff near the 24G 20.04 OS.  It may be possible to move 1 of those to the 1.8TB HDD, freeing up storage "near" the 20.04 OS so we can expand that partition and file system to be a little bigger. Expansion requires contiguous storage if we use simple partitions.  

There are more advanced ways to setup Linux that don't have this requirement, but it would need to be an install-time choice.  If you are going to get a new install perhaps of 22.04 performed, ask for LVM to be used. That single choice will provide much more flexibility at the cost of a little more complexity.  I use LVM. It has been enterprise ready and used over 20 yrs, so it isn't some alpha code. It is highly trusted, but you'll need to include some added data when asking for help with storage in the future. It is 100% fine NOT to use LVM too.

---

### Post by mvelanka on 2023-11-16
TheFu,
That is a lot of information for me ... Let me understand and digest it.
I will ask if/when I get stuck.

Another thing came to my mind was .... Can I take a new distribution CD/usb and install that (say 20.4 ) overwriting the current 18.4 ... Can I do that and keep my work and data and files intact ? Is that possible?

---

### Post by oldfred on 2023-11-16
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. **Good backups still important**
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)
[https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

---

### Post by TheFu on 2023-11-16
> **mvelanka said:**
>  Another thing came to my mind was .... Can I take a new distribution CD/usb and install that (say 20.4 ) overwriting the current 18.4 ... Can I do that and keep my work and data and files intact ? Is that possible?

a) When it comes to upgrades, people often get confused and make a mistake that completely wipes their existing files.  Don't think you are special. We've all done it at some point.  Before doing this, create backups that include not just the data, but the owner, group, permissions, ACLs, and xattrs too. **rsync** is the easiest, lightest, tool for this, but some extra options are required. And be 100% certain you know how to restore 1 file, a full directory tree, and everything. You need good backups anyway, so if you don't already have this solved, now is the time.  rsync isn't really a great backup tool, but for creating a 1-time mirror, it is quite excellent, provided the source and target files systems are native Linux (no NTFS/no exFAT).

b) Doing a dirty upgrade has many downsides.  There have been lots of subsystem changes from 18.04 to 20.04 to 22.04, so you'll end up with mixed and matched subsystems which can cause confusion as to which is actually being used.  I call it "cruft" that lets left behind.  So, while things may be possible, that doesn't make doing them a good idea.  If you have 1 system, doing things "right" is more important than if you have 10 systems with 9 of them being just for playing around.  If this is a play system, go crazy. Try things. Lose data - ooops - or not.  

It is certainly possible to NOT have data loss, but it is also possible to completely wipe everything by accident. That's the boiled down answer.

c) 2TB USB HDDs are less than $40 these days.  Sometimes the easiest answer to remove fear is to clone and old disk to a new disk and try things while the old disk sits on a shelf, completely safe from our stupidity.  I've done this in the last 8 months.  I swapped in an NVMe 1TB drive to replace a 500MB m.2 SATA SSD drive. At the time, I did a fresh install onto the NVMe, then used my restore process to selectively restore things needed on the system.  The old SATA SSD was sitting on a countertop, disconnected.  After a few months, I decided whatever was on that SATA SSD wasn't needed anymore and put it into a $12 USB USB3.2 m.2 SATA enclosure.  The speed is a bit overkill for my needs, but works well, repurposed.  It is effectively a scratch drive for temporary files that are there less than 2 days.  I already had a good backup solution, so didn't need the extra storage for that.  Anyway, I removed the risks by getting a new $70 brand SSD.  Plus, the performance upgrade from SATA to NVMe is good, even if I don't actually notice the faster speed.

---

### Post by mvelanka on 2023-11-16
TheFu
Thanks for the guidelines.
I will try to update here as I go on the forward path.
Thanks
-Mahesh

---

### Post by MAFoElffen on 2023-11-16
I have another somewhat safe recommendation... I say somewhat safe, as things do happen. Nothing is 100% sure, but... here goes... Yancek roughly recommended this in post #3, and I agree. But here is what I see there (first).

/dev/sda is a 2TB disk that is hardly used. It has a GPT partition table. It has a curious 1MiB partition at the beginning of the drive. it would be curious to see if that partition is flagged as boot_bios... I would just delete that. the second disk (/dev/sdb) has two EFI partitions (???) /dev/sdb1 is the original /EFI from Windows. /dev/sdb8 is one installed by Ubuntu. i do not know why it didn't use /dev/sdb1(?)

/dev/sda2 is 18.04 (broken, but has his data). /dev/sdb9 is 20.04 (working, new).

If he fires up the working 20.04 install he can use GParted from it to delete /dev/sda1, and shrink /dev/sda2 and move it right, to the end of the disk. Before he does that, he needs to query how much of the filesystem is being used, to know a safe size to shrink it down to...

Then create an empty vfat formatted partition at the start of that disk, about 750BM to 1GB. Flagged it as bootable and ESP. rsync /dev/sdb8 to /dev/sda1. 

Create a second partition as ext4, between the first and second partition on /dev/sda... This could be done by  either using Gparted and copy/paste /dev/sdb9 to the unallocated on /dev/sda... or create new, then rsync /dev/sdb9 to the new /dev/sda3.

From a terminal run update-grub from that instance. rsync again to update /dev/sda3. It will just sync the changed.

After that is done. copy data from /dev/sda2 (18.04) to /dev/sda3 (18.04).

Try to boot the instance on /dev/sda3 to test it.

If suscessful, reboot into the instance on /dev/sdb9 again... Gparted. Delete /dev/sd2, then grow /dev/sda3...

Second option is to after you shrink /dev/sda2 and delete /dev/sda1, then install new 22.04 LTS on /dev/sda into the unallocated on that disk, and install that how you want it to be, then copy data over to it from /dev/sda2. 

After testing is successful, the goal is to delete /dev/sda2 ( the old 18.04), the excess EFI/ESP /dev/sdb8, and /dev/sdb9 (20.04)...

Did that make sense?

---

### Post by TheFu on 2023-11-17
> The choices are nearly infinite.

The large "old" partition (2TB) is using only 375G, we know that from the provided output above.

---

