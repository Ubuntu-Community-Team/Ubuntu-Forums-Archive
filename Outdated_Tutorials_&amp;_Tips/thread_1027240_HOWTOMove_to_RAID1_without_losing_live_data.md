---
title: "HOWTO:Move to RAID1 without losing live data"
date: 2009-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Zafrusteria on 2009-01-01
When I decided it was time to make the file systems on my mail server use RAID 1 I looked around for a HOWTO. I could find loads that were either very old or incomplete or just so verbose I got old reading them. :) So in the spirit of Linux I wrote my own and published it. Here it is.

I have followed this HOWTO through for both Hardy and Intrepid. 

```
Note. Do not just follow these instructions blindly copy/pasting the commands without
reading and understanding why you are doing them. Some of the commands will fail on your 
system, due to drive device names, unique values such as UUIDs.
```

Now backup your system or better still play around with a virtual copy of your system first!

With this example I am doing this from a virtual copy of my own system. Using Vmware 2.0, Ubuntu Intrepid, it also works with Hardy. I use 4Gb expanding hard disks. I start with a new install of Intrepid that I just take a copy of and delete when I'm done playing around. :)

I'm assuming you have physically added your new new hard drive and you know which device it is. In this example we will be starting with one drive /dev/sda. It has two partitions sda1 and sda2. sda1 is mounted as root and sda2 is the swap partition. We are going to create a RAID array out of sda and a new disk sdb. These will be partitioned as sda1 - sdb1 for /dev/md0 as the root partition and sda2 - sdb2 as the root partition.

Use fdisk to set up the data and swap partition we will use as our two RAID1 partitions. Yes I'm going to put my swap partition on a RAID 1 array. I'm not going to explain why the reasons for and against are available on the net. I currently agree with arguments put up by the guys saying put swap on the RAID1 partition.

```
sudo fdisk /dev/sdb
```

To get a list of commands that fdisk accepts type 'm', just like the prompt says :)
```

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the DOS compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

```


First check it is the right disk with 'p' print the partition table. There should be nothing displayed under the headings , if this was a brand new disk.

<strong>n   add a new partition</strong> to add create the new partition.  I am using a primary partition and set it to number 1 (sdb1). We want to start this partition on cylinder 1 and make it 4000Mb in size. To make the partition 4000Mb in size, we will use the value +4000M to specify the last cylinder. Once that is done we will set the disk id type to 0xFD, so it will be "Linux RAID autodetect" type. This is the value that the Ubuntu installer uses if you were doing this at install time. So it seems to me to be a good choice. :)
```

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-522, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-522, default 522): +4000M

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux RAID autodetect)

Command (m for help): p

Disk /dev/sdb: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047915

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         511     4104576   fd  Linux RAID autodetect
```

Now add a second partition which will start just after the one above and finish at the end of the disk so you can accept the defaults. Also set the disk ID to 0xFD as before.

```
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (512-522, default 512): 
Using default value 512
Last cylinder, +cylinders or +size{K,M,G} (512-522, default 522): 
Using default value 522


Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): fd
Changed system type of partition 2 to fd (Linux RAID autodetect)

```

and one last check that all is well use the print 'p' command again.

```

Command (m for help): p

Disk /dev/sdb: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047915

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         511     4104576   fd  Linux RAID autodetect
/dev/sdb2             512         522       88357+  fd  Linux RAID autodetect

```

Now we can write this to the disk and quit fdisk.

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

This is where the fun starts we can create the RAID 1 mirrors on the two partitions. These raid array will be started degraded that is they will only have one drive. Once we have checked we can boot from it we can remove the data from the old drive and add it to the mirror as the second drive.

Install the Linux RAID software packages mdadm and initrd tools.

```
sudo apt-get install mdadm initramfs-tools
```

Create the RAID 1 array degraded, that is with just one disk, hence the 'missing' option.

```
sudo  mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 missing /dev/sdb1
```

```
mdadm: size set to 4104512K
mdadm: array /dev/md0 started.

```

Do the same for the second RAID array for the swap area. That will be using sdb2 and will be called /dev/md1. The contents of /proc/mdstat should now look something like this.

```
Personalities : [raid1] 
md1 : active raid1 sdb2[1]
      88256 blocks [2/1] [_U]
      
md0 : active raid1 sdb1[1]
      4104512 blocks [2/1] [_U]
      
unused devices: <none>
```

The file /etc/mdadm/mdadm.conf needs to be updated to include the two arrays so they are know at boot time. This updated file is also needed in the image that is loaded into the RAM disk by grub. As grub will need to know how to assemble the two RAID 1 arrays. We need to add the ARRAY lines, one for each array. To find out what these should be use the following command. Take the output and paste them into the file under the comment line about array definitions.

```
sudo mdadm --examine --brief --scan --config=partitions
```

```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=89c05226:f65e5bb6:991b8060:70a3b4f2
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=f00ee0ee:39022089:991b8060:70a3b4f2
```

Do NOT copy the lines above into your own mdadm.conf the UUIDs will be wrong!

Now to update the RAM drive image.

```
sudo update-initramfs -u
```

We need to put a file system onto the root partition of our new RAID 1 array. I use reiserfs so the command is 

```
sudo mkreiserfs -l root_raid1 /dev/md0
```

And we need to put the swap area onto /dev/md1, again I like to mount swap area by name as I think it is simpler. I have therefore added the -L swap_raid1

```
 sudo mkswap -L swap_raid1 /dev/md1
```

```
Setting up swapspace version 1, size = 88252 KiB
LABEL=swap_raid1, UUID=7816740f-2d37-4385-ab54-a56a3f01bce4

```


Reboot using the Ubuntu ALT installation disk and choose <strong>Rescue a Broken System</strong>, a rescue disk of your own or to single user mode. If you use the Ubuntu disk do not mount the old root as the root at this time. It makes the copying part a little more complex. :) I used /dev/md0
<br />
Mount the old root partition and then copy the old data over.

```
mkdir -p /mnt/old_root
sudo mount /dev/sda1  /mnt/old_root
df -h

```

```

Filesystem              Size     Used Available Use% Mounted on
tmpfs                 507.7M    44.0k    504.7M   0% /dev
/dev/scd0             696.8M   696.8M         0 100% /cdrom
/dev/sda1               3.7G     2.3G      1.4G  63% /mnt_old_root
/dev/md0                3.9G    32.1M      3.9G   1% /target
```

```
cp -a /mnt/old_root/*   /target
```

Once the copy has completed we can reboot back into the old setup and mount the array temporarily in /mnt/mirror. I find it simpler to edit in the real system as I just cannot get on with vi. :) The reboot also gives me an excuse to get another coffee. ;)

```
sudo mkdir /mnt/mirror
sudo mount /dev/md0 /mnt/mirror

```

```
Remember to do all the editing in /mnt/mirror/... so you are changing the files that will be used when you boot using the array.

```

We will need to sort out where grub is loaded from and what devices are used to boot the system. We will be accessing the /boot directory from /dev/md0 which is located on /dev/sdb1. Also the swap area is now on /dev/md1. Do not forget to update /etc/fstab so that it will point at the RAID arrays. So in reverse we do:

Edit /mnt/mirror/etc/fstab to use /dev/md0 for root. Remember I labeled the root and swap partitions so I can use those too. Below you will see the original fstab which used UUID values and examples of using LABEL or device names: 

This is the old file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  < options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e193cc1-8d37-44a9-b1b3-b1e771434712 /               reiserfs notail,relatime 0       1
# /dev/sda2
UUID=12cbd4c1-7136-4e5d-bf3f-99e2857ff066 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and it becomes one of these depending on if you use labels or dev names.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  < options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
LABEL=root_raid1     /               reiserfs notail,relatime 0       0
# /dev/md1
LABEL=swap_raid1      none            swap    sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>    < options>       <dump>  <pass>
proc            /proc           proc      defaults         0       0
# /dev/md0
/dev/md0        /               reiserfs  notail,relatime  0       0
# /dev/md1
/dev/md1        none            swap      sw               0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Update /mnt/mirror/boot/grub/menu.lst to boot from /dev/md0. You will also want to turn on the grub menu and make a few other small changes. Below are examples of the new lines for the grub menu just scroll through the file changing them as you go. The lines below are the changed lines with the new values.

```

timeout 20
# hiddenmenu
color cyan/blue  white/blue

# kopt=root=/dev/md0
# groot=(hd1,0)


```

And the menu lines themselves these are all new so add them to the top of the existing menu. Just look for the comment line. 

```
## ## End Default Options ##
title		Ubuntu 8.10, kernel 2.6.27-9-generic RAID1
root            (hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/md0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic RAID! (first disk)
root            (hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/md0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

```

We can now tell grub to find the /boot directory on the second drive, /dev/sdb.

```
sudo grub
```

and then at the grub prompt use these commands to tell grub where to load its bootstrap from.

```
root (hd1,0)
setup (hd0)
setup (hd1)

```

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd1)"...  20 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+20 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"
... succeeded
Done.

```

As we now have two almost identical root file systems, the original and the copy on the degraded RAID 1 array, I like to touch a file in both so I can check that I have them round the right way. After the reboot

```

sudo touch /mnt/mirror/this_is_mirror
sudo touch /this_is_sda1

```

Quit out of grub. You can now reboot. 

You should see the new menu, the one that talks about RAID :)
<br />
Select the first menu option and if all went well your system will come up using the RAID1 array. You will also see that you have a file called <strong>/this_is_mirror</strong>. If you have a file called <em>/this_is_sda1</em> then you have done something wrong. You missed a step or didn't do the steps in the right order.
<br />
Once you are sure you have the RAID array working, and all is well. You need to delete the old partitions on <strong>/dev/sda</strong> and make them the same as they are on <strong>/dev/</strong>sdb. You can copy the partition info from the new disk to the old disk. You will need to umount /dev/sda1 if you have remounted it after the reboot.

Use fdisk to delete the old partitions before copying the new partition table over. Remember it is <strong>/dev/sda</strong> that you need to do the deletions on.

```
sudo fdisk /dev/sda
```

```

Command (m for help): p

Disk /dev/sda: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df6a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  83  Linux
/dev/sda2             487         522      289170   82  Linux swap / Solaris

Command (m for help): d
Partition number (1-4): 2

Command (m for help): d
Partition number (1-4): 1

Command (m for help): p

Disk /dev/sda: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df6a9

Device Boot      Start         End      Blocks   Id  System

```

You may need to reboot here depending on what you have mounted. Once the system comes back up you can copy the partition table over.

```

sudo -i
sfdisk -d /dev/sdb | sfdisk /dev/sda
exit

```

```

Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 522 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63   8209214    8209152  fd  Linux RAID autodetect
/dev/sda2       8209215   8385929     176715  fd  Linux RAID autodetect
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

add the drive /dev/sda to both of the arrays (md0 &amp; md1) and allow them to to sync. You can watch this process with the command in a second terminal. Do not reboot until the resync has finished for both arrays and you see <strong>[UU]</strong> in the output from /proc/mdstat for both.

```
watch -n 7 cat /proc/mdstat
```

```

sudo mdadm --add /dev/md0 /dev/sda1
sudo mdadm --add /dev/md1 /dev/sda2

```

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda2[2] sdb2[1]
      88256 blocks [2/1] [_U]
        resync=DELAYED
      
md0 : active raid1 sda1[2] sdb1[1]
      4104512 blocks [2/1] [_U]
      [===>.................]  recovery = 19.6% (806976/4104512) finish=1.4min speed=36680K/sec
      
unused devices: <none>

```

On a real system this can take hours ~1 hour/250Gb. On VMware with a tiny disk it takes a few minutes. Time for another coffee ;o

We now have a working RAID 1 system where if one disk fails we can still carry on working. We need to make it so we can still boot from either drive when the other has failed. This is repeating some of what we have already setup but it means you can see it is done. 

We will be setting the MBR:

on the <strong>first</strong> hard disk <strong>/dev/sda</strong> or in grub terms <strong>(hd0)</strong>, to look in the first partition on the first drive for the /boot directory. (hd0,0) in grub speak.
and on the <strong>second</strong> hard disk <strong>/dev/sdb</strong> or in grub terms<strong> (hd1)</strong>, to look in the first partition on the second drive for the /boot directory, which is (hd1,0) for grub. Look at the output below for the setup commands.

The commands I used were 
```

sudo grub
root (hd0,0)
setup (hd0)
root (hd1,0)
setup (hd1)
quit

```

```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"...  20 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+20 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"
... succeeded
Done.

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd1)"...  20 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+20 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"
... succeeded
Done.
```

Do not forget to update the BIOS, so that it will try one of the two disks and if that fails try booting from the other disk. 


Useful links

[http://linux-raid.osdl.org/index.php/RAID_setup](http://linux-raid.osdl.org/index.php/RAID_setup)
mdadm man page
mdadm.conf man page
initramfs man page
initramfs.conf man page
fdisk man page
parted man page

---

### Post by talhazelden on 2009-03-20
Thanks for this HOWTO, great stuff.

Do have a question on edits to the menu.lst.

```
# kopt=root=/dev/md0
# groot=(hd1,0)
```

At what step should the new lines be un-rem'd?  Or will grub do this in the later steps?

Thanks again,
Tal

---

### Post by talhazelden on 2009-03-25
Ah, I should have read menu.list more thoroughly.  :)

---

### Post by talhazelden on 2009-03-27
worked!  cool.  Thx!

---

### Post by Robinmontreal on 2009-03-30
All seemed to work ok except, when i remove one of the drives i get a cannot find /dev/md0 when it boots up...

i did the grub for each drive as mentioned...

Any ideas what to check for?
Thanks..

---

### Post by Robinmontreal on 2009-03-30
so for further details with either disk removed it cannot boot, but with both connected/running it boots fine?

when i remove sda i get an Error 21 disk not found
when i remove sdb i get a different error, but i forget what it is...

hope this helps a bit


mdadm.conf
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=fcdaa837:e6b52678:c94fff2d:f573290e
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=31ba6ec0:ced1741a:c94fff2d:f573290e

menu.lst

## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-11-generic RAID1
root            (hd1,0)
#uuid           8e0a0cd7-10ae-4b99-86fc-2651f20ffc6a
kernel          /boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro quiet splash bootdegraded=true
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

title           Ubuntu 8.10, Kernel 2.6.27-11-generic RAID! (first disk)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro quiet splash bootdegraded=true
initrd          /boot/initrd.img-2.6.27-11-generic
quiet


fstab

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/md0  /               reiserfs    notail,relatime 0       0

/dev/md1 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda5[0] sdb5[1]
      971776 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      155252032 blocks [2/2] [UU]

unused devices: <none>

---

### Post by zoiks on 2009-04-11
Thank you, Zafrusteria, this HowTo was just what the doctor ordered for me.

---

### Post by zoiks on 2009-04-11
Actually one minor issue I had in following this HowTo was in getting the md devices up and running after booting up the ubuntu live alternate CD. Maybe you could be more explicit about how to do that. It had mdadm available, but for some reason I wasn't able to get my /dev/md0 devices started up. (I.e. so as to copy all the data from the filesystem on /dev/sda1 to the filesystem on /dev/md0, in your step that starts out as "Mount the old root partition and then copy the old data over...".)

Because I actually had two more spare partitions of identical size, /dev/sdc1 and /dev/sdd1, what I did was "dd of=/dev/sda1 if=/dev/sdd1" while I was booted up in the alternate live CD, and then rebooted into the normal system (still using /dev/sda1 for the / filesystem) and then mounted /dev/sdd1 as my old_root and /dev/md0 as my new root. Then, proceed as normal.

FWIW I was then able to expand my raid1 array to use 4 device/partitions instead of 2 (in the hopes of getting increased read performance). As it turns out, my sequential read performance did *not* improve (it's the same as the speed from a single disk) but I did get an increase in performance for reads from different processes/threads. I.e. if I read sequentially from the filesystem on /dev/md0 from four different threads, I get substantially more net throughput than a single read from a single thread. (Curiously, I get about 2x net disk throughput when I use 4 sequential read threads.)

Edit: Actually, scratch that, I'm able to get nearly 4x the single disk bandwidth for threads >= 4. In a test (done 2 times) I get, counting from 8 threads down to 1, the following speeds in MB/s:
Num Thr	8	7	6	5	4	3	2	1
Average	37.61	42.06	50.95	55.72	69.55	34.3	41.55	79.05
Total	300.85	294.4	305.7	278.6	278.2	102.9	83.1	79.05

---

### Post by jpcozar on 2009-08-29
I'd like to thank you for writting this tutorial because it's what I was looking for. In my case, I didn't use a virtual copy. I've followed your tutorial with a real Ubuntu Server 8.10 at home wich now it's working on raid 1 without lossing any data and services (nagios, smtp,pop,webmin,http, etc...). I've written a spanish tutorial describing steps I've followed here:

[http://jpcozar-public.wikidot.com/pasararaid1](http://jpcozar-public.wikidot.com/pasararaid1)

In an English google translated hehehe:

[http://translate.google.com/translate?prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fjpcozar-public.wikidot.com&sl=es&tl=en&history_state0=](http://translate.google.com/translate?prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fjpcozar-public.wikidot.com&sl=es&tl=en&history_state0=)

Other reference interesting I found:

[http://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](http://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

Thank you again!

---

### Post by shortmort37 on 2010-03-13
OK -- I've decided to take the plunge, and work through these steps (except for RAIDing the swap partition; I'm foregoing that).  Everything is going fine, until I get to this part:

> We need to put a file system onto the root partition of our new RAID 1 array. I use reiserfs so the command is 

     Code:
     sudo mkreiserfs -l root_raid1 /dev/md0 
When I do this, I get:

> ...
Guessing about desired format.. Kernel 2.6.31-20-generic-pae is running.
Format 3.6 with standard journal
Count of blocks on the device: 122095984
Number of blocks consumed by mkreiserfs formatting process: 11938
Blocksize: 4096
Hash function used to sort names: "r5"
Journal Size 8193 blocks (first block 18)
Journal Max transaction length 1024
inode generation number: 0
UUID: ca82295e-1427-494c-b576-a19abf527e28
LABEL: root_raid1
ATTENTION: YOU SHOULD REBOOT AFTER FDISK!
    ALL DATA WILL BE LOST ON '/dev/md0'!Huh?  What fdisk?  That step was 10 steps back; and I did reboot.  Or, is this a warning that after mkreiserfs invokes fdisk, I should reboot?

This is a scary warning I didn't anticipate.  Sorry to sound like such a noob, but I'm not proceeding until someone tells me I'm not going to lose my drive...

Dan

---

### Post by shortmort37 on 2010-06-23
Here's a related post to this thread:
 
>  
...I'm on page 6, where it instructs:


[SIZE=1][QUOTE][SIZE=1]Update /mnt/mirror/boot/grub/menu.lst to boot from /dev/md0.[/SIZE] [/SIZE]
Well, I ain't got no menu.lst, because I'm running 9.10 -- and grub has been deprecated for grub2. I take it I am to make my edits in /etc/grub.d/40_custom, but partition numbering has changed, and I dunno...

It was simple enough when I was just following the instructions. But now I've lost my compass.

Can someone tell me how the HowTo would change, to work with grub2 instead of grub -- i.e., what the edits are I would need to make to /etc/grub.d/40_custom?

Dan
[/QUOTE]
 
I've not received any replies.  I'm actually now running Lucid (10.04 LTS).  Can someone get me back on track, since grub has been deprecated?
 
If I can solve this problem with a hardware solution (I have a Lenovo M58p, and I'm trying to RAID 1 with an external SATA drive), I'm more than willing to shell out the cash at this point.  I just want to protect my system.
 
Thanks
Dan

---

