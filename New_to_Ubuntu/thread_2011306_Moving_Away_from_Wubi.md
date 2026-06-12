---
title: "Moving Away from Wubi"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Ubun2to on 2012-06-26
I have recently gotten messages saying I am out of space. Well, it's all because Wubi underequipped me, and now I'm out to install Ubuntu the right way. Here are my partitions:
```
Partition - PartitionName - FileSystem (notes about partitions)
/dev/sda1 - SYSTEM - ntfs (boot files, I think)
/dev/sda2 - HP - ntfs (this is where all my stuff is stored currently)
/dev/sda3 - FACTORY_IMAGE - ntfs (I'm gonna delete this soon since that is for Windows)
/dev/sda4 - Ubuntu - ext3 (my new parition)
Unallocated space - NA - unallocated (included with the computer)
```
No swap space due to a lack of partition space. I wish I had EFI-then I could have all the partitions I wanted.
I have done some research, and I have found how to move the Wubi drive to a new partition. I want to do this from my USB stick to keep the process as "clean" as possible. I have already backed up my stuff, so I want to know if I have the correct command. Note that I haven't executed the command yet. I am just really nervous that I have messed something up.
```
me@ubuntu:~$ sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda4
```
I did this using the command provided for live CDs and USBs on the [Documentation]("https://help.ubuntu.com/community/MigrateWubi"), but I don't want to screw anything up, and really want to make sure I am doing the right thing. Also, the reason I have adjusted the command from what they provide is because my partition table must be different from theirs. My target partition is sda4, not sda5. Also, if me adjusting the command will ruin it, should I adjust my partitions so sda5 is the target?
TL;DR-please inform me if I am wrong with the command and double check my partition table to make sure I have the right command, and adjusting the command because sda4 is my target. I also have no swap space-is that a requirement?

---

### Post by bcbc on 2012-06-26
Your output shows unallocated space. If you create an extended partition, then you can create a swap partition as well (You can have multiple logical partitions in an extended partition).

But since you haven't posted the details on how big the partitions are, it's unclear whether you'd have enough space (or even if /dev/sda4 is big enough).

The command as you have it will work. You are supposed to change the partition to be for your situation, i.e. /dev/sda4.
(And provided you used the same mountpoint as showed in the example)

The only issue with running from a live environment is that the architecture has to match the install (i.e. if you have a 64-bit wubi install, you need to run the migration from a 64-bit live CD).

The migration script will check the target partition (and architecture) and various other things to make sure it can proceed - before it makes any changes. (It's generally easier to run it from the Wubi install itself, but the live environment migration works fine too).

---

### Post by Ubun2to on 2012-06-27
> **bcbc said:**
> Your output shows unallocated space. If you create an extended partition, then you can create a swap partition as well (You can have multiple logical partitions in an extended partition).

But since you haven't posted the details on how big the partitions are, it's unclear whether you'd have enough space (or even if /dev/sda4 is big enough).

The command as you have it will work. You are supposed to change the partition to be for your situation, i.e. /dev/sda4.
(And provided you used the same mountpoint as showed in the example)

The only issue with running from a live environment is that the architecture has to match the install (i.e. if you have a 64-bit wubi install, you need to run the migration from a 64-bit live CD).

The migration script will check the target partition (and architecture) and various other things to make sure it can proceed - before it makes any changes. (It's generally easier to run it from the Wubi install itself, but the live environment migration works fine too).

Looks like I have to do some upgrading on my live USB (I put it in 32 bit so it would work on any computer).
Here are my partitions:
```
Partition - Label/Name - Size - Notes (from me) - Flags (from GParted, not me)
/dev/sda1 - SYSTEM - 33.59/100.00 MB - to be left untouched - boot
/dev/sda2 - HP - 223.40/761.68 GB - where Ubuntu currently is - none
/dev/sda3 - FACTORY_IMAGE - 9.69/11.32 GB - to be destroyed, resized, and merged with unallocated space - none
/dev/sda4 - Ubuntu - 2.67/158.22 GB - where I want to move Ubuntu to - none
unallocated - 196.71 MB - to be merged with sda3 - none
```
I'm going to delete sda3, rezise the unallocated space, and reserve 16 GB for swap space (I will also resize HP and Ubuntu to meet 16 GB, because swap space is supposed to be the same amount as the RAM you have or double-I have the space to double it).
sda3 is no longer needed-it's for Windows recovery. I don't need Windows anymore. I have VirtualBox taking care of my every need for Windows (which are very few, might I add).
Also, sda3 is displayed after sda4 on GParted, so I won't have any trouble with sda4 getting in the way, if you're wondering that.
I'm just going to use my x64 live DVD, as I don't have enough space to turn my live USB into x64, as I don't have the space to download it all.

---

### Post by Ubun2to on 2012-06-27
I have gotten my filesystem the way I want now.
```
Partition - Name - Size (used/total) - Filesystem - Flags (GParted) - Notes (from me)
/dev/sda1 - SYSTEM - 33.59/100.00 MB - ntfs - boot - not going to mess with this
/dev/sda2 - HP - 223.40/755.42 GB - ntfs - none - where Ubuntu currently is
/dev/sda4 - Ubuntu - 2.60/160 GB - ext3 - none - where Ubuntu is going to be moved to
/dev/sda3 - Swap - NA/16 GB - linux-swap - none - swap space
```
sda3 used to be FACTORY_IMAGE. Well, I don't use Windows anymore, so I deleted the recovery partition and made it my swap space. I'm probably going to delete sda2 fairly soon, and go all Ubuntu (in which case I might also delete SYSTEM on sda1, as I'm pretty sure that is a Lozedoze required partition).
So, this is the command I will use to move my Wubi drive to my new Ubuntu partition on sda4:
```
sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
```
In the command, /dev/sda4 is the target, and /dev/sda3 is the swap. My command is modified from this command:
```
sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda5 /dev/sda6
```
The command is from [here]("https://help.ubuntu.com/community/MigrateWubi"). sda5 is the target, and sda6 is the swap. I am going to run this from my DVD, as making my flash drive 64 bit is going to be a real pain since I have no real room left on my Wubi drive.
Am I ready to go?

---

### Post by bcbc on 2012-06-27
Looks good... 

16 GB is really a lot of swap. The 2x recommendation is good if you have a small amount of RAM. But it's not needed if you have e.g. 8 GB of RAM. I tend to add 500MB to the size of my RAM when it's over 2GB e.g. 3GB RAM -> 3.5GB swap. 
But it won't hurt if that's what you want.

---

### Post by Ubun2to on 2012-06-27
> **bcbc said:**
> Looks good... 

16 GB is really a lot of swap. The 2x recommendation is good if you have a small amount of RAM. But it's not needed if you have e.g. 8 GB of RAM. I tend to add 500MB to the size of my RAM when it's over 2GB e.g. 3GB RAM -> 3.5GB swap. 
But it won't hurt if that's what you want.

Yeah, I read that after I partitioned the swap space. But, I haven't heard of having TOO much swap space, so I guess I'm alright.

---

### Post by Ubun2to on 2012-06-27
I will now perform the command. If something goes wrong, I have everything backed up.
```
sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
```For some reason, I copied and pasted the command, and this is what I get:
```
ubuntu@ubuntu:~$ sudo bash wubi-move-2.2.sh --root-disk=/media/New\ Volume/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
bash: wubi-move-2.2.sh: No such file or directory

```Also, I'm trying to do this via a live DVD.
Edit: I realized I needed to change the directory, and that worked-sorta.
```
ubuntu@ubuntu:~$ cd /home/ubuntu/Downloads/wubi-move-2.2/
ubuntu@ubuntu:~/Downloads/wubi-move-2.2$ sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
wubi-move-2.2.sh:  Validating migration source...
wubi-move-2.2.sh:  root disk not found: /media/win/ubuntu/disks/root.disk
wubi-move-2.2.sh:  Validation of migration source failed

wubi-move-2.2.sh:  Migration did not complete successfully.
ubuntu@ubuntu:~/Downloads/wubi-move-2.2$ 

```Do I need to have my hard drive show up on the Unity launcher for this to work?
How to I find the root.disk file?

---

### Post by bcbc on 2012-06-27
That /media/win is a mount point. It's what the partition holding the root.disk is mounted on.

e.g. 
```
sudo mkdir /media/win 
sudo mount /dev/sda2 /media/win
sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda4 /dev/sda3

```
Now it will work. If you already have /dev/sda2 mounted then use the existing mountpoint e.g. if it's mounted on /media/HP then use:
```
sudo bash wubi-move-2.2.sh --root-disk=/media/HP/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
```

It depends on the actual mountpoint... and only you can know what it is :)

---

### Post by Ubun2to on 2012-06-27
> **bcbc said:**
> That /media/win is a mount point. It's what the partition holding the root.disk is mounted on.

e.g. 
```
sudo mkdir /media/win 
sudo mount /dev/sda2 /media/win
sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda4 /dev/sda3

```Now it will work. If you already have /dev/sda2 mounted then use the existing mountpoint e.g. if it's mounted on /media/HP then use:
```
sudo bash wubi-move-2.2.sh --root-disk=/media/HP/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
```It depends on the actual mountpoint... and only you can know what it is :)
I realized that-mine was /mnt/ubuntu/disks/root.disk
Anyway, I did it. However, it claims the swap space can't be made. I have read that, if the swap is on the same disk as the Ubuntu partition, it is automatically recognized as swap space. Is this correct?

---

### Post by bcbc on 2012-06-27
> **Ubun2to said:**
> I realized that-mine was /mnt/ubuntu/disks/root.disk
Anyway, I did it. However, it claims the swap space can't be made. I have read that, if the swap is on the same disk as the Ubuntu partition, it is automatically recognized as swap space. Is this correct?

The live CD will find and use any existing swap partition... I don't think a normal install will do the same thing.

Also, it won't be set up for hibernation - you'll have to do that manually which is a (little bit of a) pain.

What was the error?

Anyway - with that much RAM you won't notice it at first. Once you've got everything working fine I can assist with your setup of the swap if you need help. Kind of curious though why it didn't work though!

---

### Post by Ubun2to on 2012-06-27
> **bcbc said:**
> The live CD will find and use any existing swap partition... I don't think a normal install will do the same thing.

Also, it won't be set up for hibernation - you'll have to do that manually which is a (little bit of a) pain.

What was the error?

Anyway - with that much RAM you won't notice it at first. Once you've got everything working fine I can assist with your setup of the swap if you need help. Kind of curious though why it didn't work though!

Well, I'm out of the live CD now, so I can't post the error message.
I don't plan to do hibernation-I've heard it can be really unreliable. I'm currently using the tutorial on the [SwapFaq]("https://help.ubuntu.com/community/SwapFaq/") page.
Edit: I found out how to utilize the swap space.
I was in GParted, right clicked on my swap space, and selected "Swapon."
I then went to terminal and typed in:
```
free -m
```
And, I got this:
```
                    total       used       free     shared    buffers     cached
Mem:                7979       7261        717          0         35       1911
-/+ buffers/cache:  5314       2665
Swap:              16378          0      16378

```
So, my swap isn't being used at the moment, but it's nice to know it's there when I need it.

---

### Post by bcbc on 2012-06-28
You should add it to /etc/fstab so it's mounted automatically:

```
sudo cp /etc/fstab /etc/fstab-backup
echo "UUID=$(sudo blkid -o value -s UUID /dev/sda3)    none    swap    sw    0    0" | sudo tee --append /etc/fstab
```

Or you can manually edit it yourself. The above commands 
1. backup the /etc/fstab file in case you make a mistake, and 
2. append a line that adds your swap. 
It will end up looking like this in /etc/fstab:
UUID=xxxx-xxxx-xxxx-xxxx  none swap sw 0 0
(where xxx-xxx is the UUID of /dev/sda3)

Breakdown of the command:
"echo" outputs a "" string to standard output (screen)
Inside that string "sudo blkid" extracts the UUID of your swap partition
"|" pipes the output to tee
"tee --append" will append the output to the end of the /etc/fstab file

The blkid command and the tee command require root privileges (hence the use of sudo)

---

### Post by Ubun2to on 2012-06-28
> **bcbc said:**
> You should add it to /etc/fstab so it's mounted automatically:

```
sudo cp /etc/fstab /etc/fstab-backup
echo "UUID=$(sudo blkid -o value -s UUID /dev/sda3)    none    swap    sw    0    0" | sudo tee --append /etc/fstab
```

Or you can manually edit it yourself. The above commands 
1. backup the /etc/fstab file in case you make a mistake, and 
2. append a line that adds your swap. 
It will end up looking like this in /etc/fstab:
UUID=xxxx-xxxx-xxxx-xxxx  none swap sw 0 0
(where xxx-xxx is the UUID of /dev/sda3)

Breakdown of the command:
"echo" outputs a "" string to standard output (screen)
Inside that string "sudo blkid" extracts the UUID of your swap partition
"|" pipes the output to tee
"tee --append" will append the output to the end of the /etc/fstab file

The blkid command and the tee command require root privileges (hence the use of sudo)

```
UUID=b3c81570-72f2-4425-9331-6309672e95b7    none    swap    sw    0    0

```
```
root@ubuntu:/home/administrator# free -m
                                           total       used       free     shared    buffers     cached
Mem:                                 7979       7752        226          0        253       1528
-/+ buffers/cache:        5970       2008
Swap:                                         0          0          0

```

---

### Post by bcbc on 2012-06-28
To activate:
```
sudo swapon -a
```

Or when you reboot it gets pulled automatically from the /etc/fstab...

---

### Post by Ubun2to on 2012-06-28
> **bcbc said:**
> To activate:
```
sudo swapon -a
```

Or when you reboot it gets pulled automatically from the /etc/fstab...

Thanks. The command worked.

---

