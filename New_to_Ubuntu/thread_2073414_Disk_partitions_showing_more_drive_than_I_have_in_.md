---
title: "Disk partitions showing more drive than I have in GParted"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by StinkySQL on 2012-10-19
In attempting to learn Gnu/Linux I have run into something that makes no sense to me (coming from a DOS/Windows world). Nothing is broken, I just want to understand what it is that I am seeing.

I have one 75GB drive with Ubuntu 12.04 installed. Not a dual boot system, so it is just this one installation on the box. GParted shows that /dev/sda is 74.5 GB. I expected to see one partition and maybe a swap but GParted shows the following.

[LIST]
[*]/dev/sda1    ext4            35.03 GB    1GB used (This has a Flags=boot )
[*]/dev/sda2   extended   39.05 GB     - for used column
[*]  /dev/sda6 ext4             35.63 GB     5.86 used (This has a mount point entry of / )
[*]  /dev/sda5 linux-swap   3.87 GB     - for used column
[/LIST]
The SDA 5 and 6 are indented as shown, but I don't know what that might mean. All partitions show a key except the boot partition sda1. Is sda2 just a logical location for 5 and 6? Seems so. But I don't understand where exactly my files are because I don't "see" two logical drives in the traditional Windows sense.

Can anyone explain or reference some literature that would do the same?

Thanks in advance.
Mike

---

### Post by Cavsfan on 2012-10-19
In terminal enter **sudo blkid** and then edit fstab **gksu gedit /etc/fstab** and make sure it reflects the correct partitions.

---

### Post by StinkySQL on 2012-10-19
FSTAB shows sda5 and sda6 and matches blkid by UUID. The blkid shows 1,5,6 and 0 (cdrom) but not 2 so that must be alias.

/dev/sda1: UUID="e9f0115e-d046-4c59-a3b7-f7d8d79ef999" TYPE="ext4" 
/dev/sda5: UUID="6de12b07-96f1-4797-809a-02f22754a3fb" TYPE="swap" 
/dev/sda6: UUID="8b168c51-ad5a-4fee-831b-e68ede3eb56d" TYPE="ext4" 
/dev/sr0: LABEL="REVOLUTION_OS_DISC_2" TYPE="udf" 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8b168c51-ad5a-4fee-831b-e68ede3eb56d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6de12b07-96f1-4797-809a-02f22754a3fb none            swap    sw              0       0

---

### Post by cmont899 on 2012-10-19
/dev/sda2 is an extended partition containing sda5 and sda6.


[http://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition](http://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition)

---

### Post by StinkySQL on 2012-10-19
OK - makes sense. Thanks for the heads up.

---

### Post by dannyboy79 on 2012-10-19
if the partition sda1 isn't being mounted anywhere it appears as though you're just wasting that space. not sure how that happened but it did.

---

### Post by larrys4227 on 2012-10-19
> **StinkySQL said:**
> 

I have one 75GB drive with Ubuntu 12.04 installed. Not a dual boot system, so it is just this one installation on the box. 

[LIST]
[*]/dev/sda1    ext4            35.03 GB    1GB used (This has a Flags=boot )
[*]/dev/sda2   extended   39.05 GB     - for used column
[*]  /dev/sda6 ext4             35.63 GB     5.86 used (This has a mount point entry of / )
[*]  /dev/sda5 linux-swap   3.87 GB     - for used column
[/LIST]



I'm curious .... what do you have installed to sda1 thats taking up 35G of precious drive space? sda6 is your /root (and I assume) your /home. linux swap should be on a primary partition .... but ok, if your not having troubles hibernating/suspending.

Like I said .... just curious as to why half the drive isnt used. :)

---

### Post by larrys4227 on 2012-10-19
Oops  danny ... we were thinking the same. :)

---

### Post by AndyOpie150 on 2012-10-19
They have three distinct partitions. sda1 with 35.03GB and is the primary partition. sda6 which is a logic partition. sda5 which is the swap partition.

sda5 and ada6 are in the extended partiton called sda2, sda5 being the swap.

sda1 is only 35.03GB, meaning that 35.03GB is all that is available to the OS that is in that partition.
sda6 is only 35.63GB, meaning that 35.63GB is all that is available to the OS that is in that partition.

They are clearly running two different operating system as can be seen by the fact that sda1 has 1GB used and sda6 has 5.86 used.

I would look at the Ubuntu boot screen and see what it says is on the partitions. Could be one of the partitions was a failed attempt at installing Ubuntu, or when checking out Ubuntu it was installed without realizing? Or Someone else had put another operating system on it without your realizing it. 

The bottom line is there are three separate partitions. One is a swap and the other two are ext.4.

There are not just two with one being a swap and the other being 71.13GB.

EDIT: Sorry didn't see the last four post for some reason.

The best thing to do is burn a cd with the boot-repair .iso found here: [http://ubuntuforums.org/showpost.php?p=12217150&postcount=2](http://ubuntuforums.org/showpost.php?p=12217150&postcount=2)
Then find out which partition has the Distro you are currently using. Wipe and format (to ext.4 ), and merge the other to it.

The boot repair is for in case you mess up and wind up in grub rescue.

You might have to change the Primary to a logic and the logic to a primary as you can not merge a primary into a logic, but, you can merge a logic into a primary. At least I'm pretty sure that's how it goes.

---

### Post by larrys4227 on 2012-10-19
> **StinkySQL said:**
>  Not a dual boot system, so it is just this one installation on the box. GParted shows that /dev/sda is 74.5 GB. I expected to see one partition and maybe a swap but GParted shows the following.
SNIP


I believe thats why he was asking the question .... sda1 wasnt expected when he looked in GParted. If there is an OS in sda1 @ 1GB, I'd like to know what it is. LOL!

The extended/logicals probably happened at the install ... it clearly cut the drive in half.

---

### Post by StinkySQL on 2012-10-19
> **larrys4227 said:**
> ... If there is an OS in sda1 @ 1GB, I'd like to know what it is. LOL!


So did I so I took this machine down and looked at GRUB a lot closer. 

When I installed this machine, I thought the drive was scrubbed. I did not remember that I had installed an Unbuntu Server test a month earlier. DOH!

---

### Post by larrys4227 on 2012-10-19
> **StinkySQL said:**
>  DOH!

DOH!  :guitar:

---

### Post by StinkySQL on 2012-10-19
LOL - exactly, and now I do have a problem. Gluing the two back together!

---

### Post by larrys4227 on 2012-10-19
Sounds like its a pretty new install .... maybe start all over again?

Wipe the disk clean with GPartedLive and then make 3 primary partitions.

sda1 - /(root-ext4) 15G (for install of 12.04)
sda2 - swap  1-4G depending on your memory
sda3 - /home (ext4) Remaing HD space

Couple years ago I started a seperate /home ... wish I had done it way before that too.

Nowadays I have multiple distro logical partitions with one common /home and its awesome on many levels for testing and playing with all the great Linux Distros that come out.

Of course I have my main distro .. and thats parked on sda1.

Anyway, have fun! :popcorn:

---

### Post by StinkySQL on 2012-10-19
I was able to marry the two partitions using GParted after booting to a Live-CD. Then I had to go through a boot-repair session to get grub pointing correctly again. Whoever wrote boot-repair was genius. 

Never lost a byte of info. I love Ubuntu. It gives me such a sense of accomplishment. ;)

---

### Post by Cavsfan on 2012-10-20
> **StinkySQL said:**
> I was able to marry the two partitions using GParted after booting to a Live-CD. Then I had to go through a boot-repair session to get grub pointing correctly again. Whoever wrote boot-repair was genius. 

Never lost a byte of info. I love Ubuntu. It gives me such a sense of accomplishment. ;)

Glad you got it sorted out. I thought maybe you had a previous Ubuntu installation in which case fstab would have double entries.
It retains the older ones as well as the new ones but, come to think of it I don't believe GParted would show that.

Sda1 being used in a prior install makes a lot of sense. 
Happy Ubuntuing! :D

---

