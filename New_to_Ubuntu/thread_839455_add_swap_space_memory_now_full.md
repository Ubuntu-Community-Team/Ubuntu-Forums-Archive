---
title: "add swap space/ memory now full?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by zholden on 2008-06-24
Hi Folks, 
I'm a rookie, and I really need some help. 

Last night, following directions on a previous Ubuntu forum post, I added a large swap space file (from 2GB to 12GB) to my machine using:

sudo dd if=/dev/zero of=/swap_file bs=1M count=1000

This did not solve my problem, so I rebooted and the original 2G swap space is available. However, I can no longer write or copy any files to my machine. I get an error message telling me that my memory is full, although I've got 300GB of drive space left. 

I just don't have the diagnostic tools to find out what I did, or how to correct the problem. 

Can anyone help me out here? I'm dead in the water...

Z

---

### Post by the_doc on 2008-06-24
I'm not sure what went wrong, but for reference according to some documentation I dug up:

> The size of your swap space should be equal to twice your computer's RAM, or 32 MB, whichever amount is larger, but no more than 2048 MB (or 2 GB).

---

### Post by drs305 on 2008-06-24
Please post:
```
cat /etc/fstab
sudo blkid
sudo fdisk -l
```

You don't need a 12GB swap file...

---

### Post by Cypher on 2008-06-24
Unlike Windows, the SWAP space in Linux is not a file, rather it's a partition that is formatted differently.

You would ideally use "fdisk" to create a SWAP partition in the size that you want. The double-of-RAM rule only applies if you are running on a machine with < 512MB of memory. Otherwise, something liek 512MB should be completely fine.

Once you've created the partition you'd use "mkswap" to format the newly creately partition and then "swapon" to activate it. You should also modify the "/etc/fstab" file to make use of the SWAP partition.

Not sure which forum post you were following..

---

### Post by zholden on 2008-06-24
Thanks for the reply. When I created the swap file, I did as you suggested using mkswap and then swapon. I did not make this change permanent, though, I figured I'd turn it on when needed, using the swapon on command? Obviously, I'm pretty clueless here. 

Can you suggest a way of removing the 12GB swap file I created, or more generally to undo what I've done? I need my computer back!

Z

---

### Post by zholden on 2008-06-24
Hey DRS305, what does that code you posted do? I'm pretty wary of tinkering after messing up the first time.

Z

---

### Post by the_doc on 2008-06-24
> **zholden said:**
> Hey DRS305, what does that code you posted do? I'm pretty wary of tinkering after messing up the first time.

Z

Those commands are a way of analysing your currrent set up, they wont change anything.

If you are ever in need of more info on a command type 

**man <command>**

**man fdisk** for example.

in the shell to find out more.

---

### Post by drs305 on 2008-06-24
The fstab command shows us what is being mounted at boot. The swap partition is normally mounted on boot. If it isn't listed or is listed incorrectly then it won't automatically be enabled on start.

Fdisk shows how your current partitions are set up - what they are and where they are mounted. One of them should be the swap partition. We first would look to see if and on what partition swap resides, and then look at fstab to see if the fstab instructions point to the correct location.

The blkid lists the UUID, or identifier, of the partitions. Often when someone tinkers with a partition the UUID number changes. Unfortunately, fstab doesn't automatically know of the change and may be unable to locate the partition when the UUID changes. So we have to compare the two results to make sure the UUIDs are correct.

None of these commands does anything but report information. But it is never wrong to know what a command does before executing it ;-)

---

### Post by zholden on 2008-06-24
Just in case you're willing to keep helping me here...I entered the commands you sent and here's what I see:
cat /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8829b12f-ebb7-4d2e-bf84-39a91c518ef8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=b90ca82c-d7f6-4fb0-93c0-6d72b969ed2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
zack@zack-desktop:~$ sudo blkid
/dev/sda1: UUID="CCBCCAE2BCCAC5E4" TYPE="ntfs" 
/dev/sda2: UUID="2e0a573d-5392-45b2-807d-8585f8f0642e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="8829b12f-ebb7-4d2e-bf84-39a91c518ef8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d46621b5-a0be-4678-817d-4990a76f77d7" 
/dev/sda6: TYPE="swap" UUID="b90ca82c-d7f6-4fb0-93c0-6d72b969ed2b" 
zack@zack-desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Any interpretation or suggestions? 
Thank you for helping me. 
Z

---

### Post by komputes on 2008-06-24
Please make sure to define memory as RAM or Hard disk space as they are different. Which one is full?

I would go about this differently. Personally I have always used a partition for SWAP and not a file. I'm guessing that you have a default Ubuntu installation which has created a swap space and asses to /etc/fstab to be mounted automatically. All this magic is done in the back end so you never really get to see it in detail while you are installing. Usually you will see that a swap partition was created at the last screen of of the installer.

Now that we're passed that, I had to expand my swap space so this is how I did it.

1) Boot from a Live CD

2) Start up a terminal by going to Applications> Accessories > Terminal

3) Run the following command to unlock the swap partition so that it can be resized:
```
sudo swapoff -a
```4) Then go into the Partition Editor (gparted) and change the size of your partitions.

In your case you would expand /dev/sda6. Note you may need to make /dev/sda4 (or another neighboring partition) smaller to do so 

I found this the easiest way to resize my swap partition after an installation has already been made. Can anybody tell me what would be the benefit of a swap file?

---

### Post by bodhi.zazen on 2008-06-24
> **Cypher said:**
> Unlike Windows, the SWAP space in Linux is not a file, rather it's a partition that is formatted differently.

You would ideally use "fdisk" to create a SWAP partition in the size that you want. The double-of-RAM rule only applies if you are running on a machine with < 512MB of memory. Otherwise, something liek 512MB should be completely fine.

Once you've created the partition you'd use "mkswap" to format the newly creately partition and then "swapon" to activate it. You should also modify the "/etc/fstab" file to make use of the SWAP partition.

Not sure which forum post you were following..

FYI you can use a swap file or a swap partition. A swap partition will be theoretically faster (although with modern computers you will likely not notice much difference).

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

---

### Post by zholden on 2008-06-24
RE: memory, I'm not sure. If I copy a file then paste to another folder, I get an error message: "there is not enough space on the destination"

I've been thinking of upgraging from gutsy to heron...will this chickens##t alternative fix restore defaults and fix my problem? 

Thank you again for helping me out,
Z

---

### Post by drs305 on 2008-06-24
> **zholden said:**
> Just in case you're willing to keep helping me here...

Absolutely.
> 
zack@zack-desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Any interpretation or suggestions? 
Thank you for helping me. 
Z

I should have anticipated this. The command (**fdisk -l**) switch is a small L, not a 1 (one). So the fdisk didn't understand -1 (one) and had to ask what you really wanted, and gave you some suggestions (see how helpful ubuntu can be ;-) )

---

### Post by zholden on 2008-06-24
Ahh...
fdisk -l -- Ubuntu says: 
"partion table entries are not in disc order "

What does that mean?

---

### Post by komputes on 2008-06-24
> **zholden said:**
> RE: memory, I'm not sure. If I copy a file then paste to another folder, I get an error message: "there is not enough space on the destination"

zholden: I'm thinking you are out of hard disk space since you cannot copy a file to a destination because the disk is full. Can you post the output of the following command:

Edit: ```

df -h
``` (oops, i can't type today)

---

### Post by bodhi.zazen on 2008-06-24
> **zholden said:**
> Ahh...
fdisk -l -- Ubuntu says: 
"partion table entries are not in disc order "

What does that mean?

Nothing significant. If you look at your partitions by start and end cylinder you will see they are out of order.

You can fix it with fdisk if you like, but it is not necessary.

sudo fdisk /dev/sda

at the menu type x (for expert menu) ; m to list commands

fix -> exit -> write changes to disk -> exit fdisk

reboot (you should reboot after re-writing your partition table).

---

### Post by zholden on 2008-06-24
I've got tons of space left on the hard drive, it must not know where to store data...
dev/sda6 
bash: no such file or directory

---

### Post by zholden on 2008-06-24
code: df -h

result:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              45G   45G     0 100% /
varrun                3.9G   80K  3.9G   1% /var/run
varlock               3.9G     0  3.9G   0% /var/lock
udev                  3.9G   96K  3.9G   1% /dev
devshm                3.9G     0  3.9G   0% /dev/shm
lrm                   3.9G   38M  3.9G   1% /lib/modules/2.6.22-14-generic/volatile
overflow              1.0M   52K  972K   6% /tmp

So what happened to sda5 and sda6? I've got 200+ GB of HD space allocated to Ubuntu...I don't know where that 45GB came from...

---

### Post by Greyed on 2008-06-24
> **Cypher said:**
> Unlike Windows, the SWAP space in Linux is not a file, rather it's a partition that is formatted differently.

For the record this is incorrect.  Unlike Windows swap in Linux can be either a file or a partition.

General convention is to place the swap file on a partition to bypass the cost of looking up its location on the file system.  However there are some who feel that when you're touching swap on a regular basis the cost of looking up the location on the hard drive is inconsequential to the cost of actually using swap thus there is no *practical* benefit of going through the complexity of creating and maintaining a separate partition.  As such creating, or expanding, swap by using a swap file is a viable option.

---

### Post by drs305 on 2008-06-24
> **zholden said:**
> 
So what happened to sda5 and sda6? I've got 200+ GB of HD space allocated to Ubuntu...I don't know where that 45GB came from...

From these results, sda5 and sda6 have been made into swap partitions:
```

zack@zack-desktop:~$ sudo blkid
/dev/sda1: UUID="CCBCCAE2BCCAC5E4" TYPE="ntfs"
/dev/sda2: UUID="2e0a573d-5392-45b2-807d-8585f8f0642e" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="8829b12f-ebb7-4d2e-bf84-39a91c518ef8" SEC_TYPE="ext2" TYPE="ext3"
[B]/dev/sda5: TYPE="swap" UUID="d46621b5-a0be-4678-817d-4990a76f77d7"
/dev/sda6: TYPE="swap" UUID="b90ca82c-d7f6-4fb0-93c0-6d72b969ed2b"[/B]
zack@zack-desktop:~$ sudo fdisk -1

```

If you had important data on these partitions someone with better knowledge of recovery options will have to chime in here... :(

---

### Post by zholden on 2008-06-24
> **drs305 said:**
> From these results, sda5 and sda6 have been made into swap partitions:
```

zack@zack-desktop:~$ sudo blkid
/dev/sda1: UUID="CCBCCAE2BCCAC5E4" TYPE="ntfs"
/dev/sda2: UUID="2e0a573d-5392-45b2-807d-8585f8f0642e" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="8829b12f-ebb7-4d2e-bf84-39a91c518ef8" SEC_TYPE="ext2" TYPE="ext3"
[B]/dev/sda5: TYPE="swap" UUID="d46621b5-a0be-4678-817d-4990a76f77d7"
/dev/sda6: TYPE="swap" UUID="b90ca82c-d7f6-4fb0-93c0-6d72b969ed2b"[/B]
zack@zack-desktop:~$ sudo fdisk -1

```

If you had important data on these partitions someone with better knowledge of recovery options will have to chime in here... :(
DRS: will the code you posted above correct sda5 and sda6? 
I can still see my data on the disc, I should be able to save it to an external drive, then put it back when all is well, shouldn't I? 

I hope I don't pay the price for tinkering...

---

### Post by komputes on 2008-06-24
> **zholden said:**
> code: df -h

result:
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda4              45G   45G     0 100% /**
varrun                3.9G   80K  3.9G   1% /var/run
varlock               3.9G     0  3.9G   0% /var/lock
udev                  3.9G   96K  3.9G   1% /dev
devshm                3.9G     0  3.9G   0% /dev/shm
lrm                   3.9G   38M  3.9G   1% /lib/modules/2.6.22-14-generic/volatile
overflow              1.0M   52K  972K   6% /tmp


As I thought your principal hard disk is full, you should probably delete that 12GB swap file as it is not being used (you have a swap partition).

---

### Post by drs305 on 2008-06-24
> **zholden said:**
> DRS: will the code you posted above correct sda5 and sda6? 
I can still see my data on the disc, I should be able to save it to an external drive, then put it back when all is well, shouldn't I? 

I hope I don't pay the price for tinkering...

The commands I listed won't fix anything. If you can still see the files you should be able to save them. I would copy them to another place before doing anything else. 

The fix may be as simple as changing the partitions from swap back to ext3 but I didn't want to give that advice in case it wrote new information to the partitions and corrupted any data there.

---

### Post by komputes on 2008-06-24
I can't guarantee anything but try the following to get those large partitions back up. I'm guessing these were ext3 partitions. I estimate you can bring them back up by doing this as long as they haven't been formated. (it's worth a try...)

```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

```Replace the contents of the file with this and reboot:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8829b12f-ebb7-4d2e-bf84-39a91c518ef8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=b90ca82c-d7f6-4fb0-93c0-6d72b969ed2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
zack@zack-desktop:~$ sudo blkid
/dev/sda1: UUID="CCBCCAE2BCCAC5E4" TYPE="ntfs" 
/dev/sda2: UUID="2e0a573d-5392-45b2-807d-8585f8f0642e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="8829b12f-ebb7-4d2e-bf84-39a91c518ef8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="ext3" UUID="d46621b5-a0be-4678-817d-4990a76f77d7" 
/dev/sda6: TYPE="ext3" UUID="b90ca82c-d7f6-4fb0-93c0-6d72b969ed2b" 
```Please let me know if this beings your drives back up. If you cannot see the drives, you can revert to the old fstab file by running "sudo mv /etc/fstab.bak /etc/fstab".

If it does work, you will need to create a swap partition using these[ instructions]("http://ubuntuforums.org/showpost.php?p=5253418&postcount=10"). Please note that you can only have 4 primary partitions, so you may need to create a logical container to hold the rest of the partitions. Either way, I would recommend backing up to external storage before you attempt this.

---

### Post by zholden on 2008-06-24
> **komputes said:**
> As I thought your principal hard disk is full, you should probably delete that 12GB swap file as it is not being used (you have a swap partition).
komputes, are you able to give me a command that deletes the loathesome swap file I created? I'd love to get rid of it after the pain it's caused. 
Thanks for chiming in, I'm very grateful for the help. 
Z

---

### Post by Greyed on 2008-06-24
> **zholden said:**
> komputes, are you able to give me a command that deletes the loathesome swap file I created? I'd love to get rid of it after the pain it's caused. 
Thanks for chiming in, I'm very grateful for the help. 
Z

Well, you created it with this command:
```
sudo dd if=/dev/zero of=/swap_file bs=1M count=1000
```

The relevant portion is of=**/swap_file**.  That means "output file equals /swap_file"

So the following should be safe to perform:
```
sudo swapoff /swap_file
sudo rm /swap_file
```

Presuming, of course, that is the exact command you ran.  In fact, prior to running those commands try this one to ensure the file is there:

```
ls /swap_file
```

Only being extra cautious since we're getting lots of fingers in the pie and your data partitions were listed as swap.  Time to be extra careful.  :)

---

### Post by komputes on 2008-06-24
--
EASY WAY
--
ALT-F2 and enter in the box:
gksudo nautilus

It will open a windows as the root user (you can delete anything so be careful).
Find the swap file (within this window) and delete it/empty the trash.

--
DANGEROUS WAY
--
arg. well i'm going to be yelled at for this because everyone says not to run this command. SO BE VERY SURE THAT THIS IS THE SWAP FILE!!!

Be sure you can locate the EXACT PATH before using this command as it will delete the file and not be able to bring it back (unlike the trash).

```
sudo rm -f */whrere/there/swap/file/is/located/swapfile.swap*
```

---

### Post by zholden on 2008-06-24
Woohoo! I did as you said, and Ubuntu is happy again. 

Thank you, kompute and DRS305, I'm truly astonished that you'd take the time to help a stranger solve a problem that is just beyond my abilities. Wish I could buy you a beer. 

Your command got rid of the swap file too. 

No more messing with swap spaces for awhile. 

Gratefully,

Zack

---

### Post by komputes on 2008-06-24
> **zholden said:**
>  I'm truly astonished that you'd take the time to help a stranger solve a problem

That's what Ubuntu is all about.

---

