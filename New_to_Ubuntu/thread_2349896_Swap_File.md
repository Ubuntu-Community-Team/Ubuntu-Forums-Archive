---
title: "Swap File"
date: 2017-01-19
forum: New to Ubuntu
---

### Post by scriber on 2017-01-19
Totally new user here, Ubuntu 16.04.1

I've been working my way through various things since I installed it a month or so ago, but cannot figure out the swap file.

I installed Ubuntu on a 100GB partition and also a 20Gb partition for the swap file when I did the installation.

I'm not having any problems that I know of, but am wondering if it is actually using the swap file partition.

Probably a simple answer but after searching various threads I am still not sure.

Other info ( if needed ) is I am running BootIt Bare Metal ( Terabyte Unlimited Boot manager ) with unlimited Primary partitions, with BM, XP, Vista, Win7(games),Win7Business, Ubuntu and the swap file in that order on Primary partitions.

Absolutely no problems running the different OS's.

---

### Post by bearlake on 2017-01-19
> **scriber said:**
> Totally new user here, Ubuntu 16.04.1

I've been working my way through various things since I installed it a month or so ago, but cannot figure out the swap file.

I installed Ubuntu on a 100GB partition and also a 20Gb partition for the swap file when I did the installation.

I'm not having any problems that I know of, but am wondering if it is actually using the swap file partition.

Probably a simple answer but after searching various threads I am still not sure.

Other info ( if needed ) is I am running BootIt Bare Metal ( Terabyte Unlimited Boot manager ) with unlimited Primary partitions, with BM, XP, Vista, Win7(games),Win7Business, Ubuntu and the swap file in that order on Primary partitions.

Absolutely no problems running the different OS's.

To see if you are using any swap just copy and paste this in the "terminal".

```
free mem
```

---

### Post by scriber on 2017-01-19
```
free: command not found
```

Is what I get when typing your command in the Terminal.

---

### Post by Tadaen_Sylvermane on 2017-01-19
I've never noticed my laptop using swap for anything. From everythign I've read swap is only useful if you hibernate anyway. I only gave my laptop and server both 2 gigs and I feel that is a waste. 20 is completely unnecessary imo.

```
free mem
``` is what it should be.

---

### Post by bearlake on 2017-01-19
> **Tadaen_Sylvermane said:**
> I've never noticed my laptop using swap for anything. From everythign I've read swap is only useful if you hibernate anyway. I only gave my laptop and server both 2 gigs and I feel that is a waste. 20 is completely unnecessary imo.

```
free mem
``` is what it should be.

Yes "free mem" without the "".

Having trouble posting at this time. sorry

Will try again later. :(

---

### Post by SeijiSensei on 2017-01-19
You can also see memory usage by running the "top" command which takes a snapshot of running processes each second as well:

```

top - 12:20:54 up 155 days, 14:48,  1 user,  load average: 0.07, 0.02, 0.00
Tasks: 188 total,   1 running, 187 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  0.0%sy,  0.0%ni, 99.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6109976k total,  5970340k used,   139636k free,   772740k buffers
Swap:   262140k total,    14256k used,   247884k free,  3601972k cached

```

This is a virtual server with a lot of regular memory so swap isn't used much.  In fact, 3.6 GB of memory is being used to cache disk transactions.

On laptops swap is used to store the memory image when hibernating, so it needs to be at least as large as the actual physical memory.

Swap of 20 GB is overkill.  On machines with less than 4 GB of physical memory I'd probably have at least 4 and maybe 8 GB of swap at most.

---

### Post by scriber on 2017-01-19
Thanks for the reply, running free mem gives me 


```
              total        used        free      shared  buff/cache   available
Mem:        4045864     1313816     1574844       30344     1157204     2424544
Swap:             0           0           0
```

---

### Post by scriber on 2017-01-19
> **SeijiSensei said:**
> Swap of 20 GB is overkill.  On machines with less than 4 GB of physical memory I'd probably have at least 4 and maybe 8 GB of swap at most.

Okay, I wasn't sure about the swap file size when I did the installation, I will change that to a lower number, I have 4GB of physical memory.

I ran the top command but couldn't seem to copy the result as it was still running and wouldn't let me copy.

The last line shows " KiB Swap:  0 total,  0 free, 0 used. 2328840 avail Mem

---

### Post by SeijiSensei on 2017-01-19
Hit Ctrl-C to stop top; then you can copy the page.  Since it refreshes the screen once each second, it's hard to grab it while running.

---

### Post by HermanAB on 2017-01-19
Everything you never wanted to know about swap, is explained very nicely in the swapon man page:
> man swapon

---

### Post by scriber on 2017-01-19
> **SeijiSensei said:**
> Hit Ctrl-C to stop top; then you can copy the page.  Since it refreshes the screen once each second, it's hard to grab it while running.

Thank you for that, much appreciated !

It's taking me awhile to get used to using a Terminal again, last time was when I used an Amiga and early Dos days :)

---

### Post by ajgreeny on 2017-01-19
Your free mem output shows that you do not have any swap```
              total        used        free      shared  buff/cache   available
Mem:        4045864     1313816     1574844       30344     1157204     2424544
Swap:             0           0           0
```
Can we see the output of ```
cat /etc/fstab
```which will show us if it is set to be used when you boot and then command ```
sudo blkid -c /dev/null
```which will help us figure out your rather complicated partition structure, and will certainly help me understand your comments:-
> Other info ( if needed ) is I am running BootIt Bare Metal ( Terabyte Unlimited Boot manager ) with unlimited Primary partitions, with BM, XP, Vista, Win7(games),Win7Business, Ubuntu and the swap file in that order on Primary partitions.which does not mean much to me as I know nothing of BootIt Bare Metal ( Terabyte Unlimited Boot manager ).

---

### Post by scriber on 2017-01-19
> **HermanAB said:**
> Everything you never wanted to know about swap, is explained very nicely in the swapon man page:

Thank you for that, taking me a while to figure some things out.

If I may ask, what is the command to see what partitions are being used, which is what I should have asked at the beginning ?

---

### Post by scriber on 2017-01-19
> **ajgreeny said:**
> Your free mem output shows that you do not have any swap```
              total        used        free      shared  buff/cache   available
Mem:        4045864     1313816     1574844       30344     1157204     2424544
Swap:             0           0           0
```
Can we see the output of ```
cat /etc/fstab
```which will show us if it is set to be used when you boot and then command ```
sudo blkid -c /dev/null
```which will help us figure out your rather complicated partition structure, and will certainly help me understand your comments:-
which does not mean much to me as I know nothing of BootIt Bare Metal ( Terabyte Unlimited Boot manager ).

Sorry if I'm not posting things correctly, I see that someone (Mod ? ) edited some of my posts.

When I type the first command you gave I get this 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=98b036be-3fbd-43dc-bea0-30ba3f7abb5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=998ca371-4c13-4360-b152-52ad3daad866 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

When I type the second command you give, I get this 

```
/dev/sda1: UUID="98b036be-3fbd-43dc-bea0-30ba3f7abb5b" TYPE="ext4" PTTYPE="dos" PARTUUID="6f875cd6-01"
/dev/sdb1: PARTUUID="1741603d-f5ec-4efc-9130-6d15b3ac01f1"
/dev/sdb2: LABEL="Data3" UUID="21B78EF713C2C8B5" TYPE="ntfs" PARTUUID="0e55aefb-3958-4986-9ca6-cdfacf4b6128"
/dev/sdc1: LABEL="Game Data" UUID="9644389844387D55" TYPE="ntfs" PARTUUID="ed96ed96-01"
/dev/sdd1: LABEL="Data 2" UUID="BC60309860305B7A" TYPE="ntfs" PARTUUID="1903c4b9-01"
/dev/sde1: LABEL="Games2" UUID="CE3C2B0E3C2AF0DF" TYPE="ntfs" PARTUUID="942493ea-01"
/dev/sdf1: LABEL="STORE N GO" UUID="97E5-9723" TYPE="vfat" PARTUUID="c3072e18-01
```

Hopefully I did this right !

---

### Post by deadflowr on 2017-01-19
> Sorry if I'm not posting things correctly, I see that someone (Mod ? ) edited some of my posts.
I did. Two posts, but only to fix the code tags.
One post was broken and the other post formats better with code tags.
Seems you figured it out. though. (On how to use code tags)

That said, you do not have a swap partition, even though it's marked in fstab.

---

### Post by scriber on 2017-01-19
> **deadflowr said:**
> I did. Two posts, but only to fix the code tags.
One post was broken and the other post formats better with code tags.
Seems you figured it out. though. (On how to use code tags)

That said, you do not have a swap partition, even though it's marked in fstab.

Thank you for teaching me to use code tags, I do appreciate it !

So what do I do to enable the swap partition that's there but apparently not being used ?

---

### Post by #&amp;thj^% on 2017-01-19
> **scriber said:**
> Thank you for teaching me to use code tags, I do appreciate it !

So what do I do to enable the swap partition that's there but apparently not being used ?

/Not so sure if it is there.
Mine looks like this:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>  <type>  <options>  <dump>  <pass>
UUID=c4e5cf73-80f4-4f4f-9cb0-6a246153a94e /              ext4    defaults,noatime 0       1
[COLOR=#ff0000]UUID=dbffdd5e-5fd3-4a34-a136-66f19955da8c swap           swap    defaults,noatime 0       0[/COLOR]


```
Yours shows where it thought it was during the install:
```
# swap was on /dev/sda2 during installation

UUID=998ca371-4c13-4360-b152-52ad3daad866 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
I agree with ajgreeny I don't seem to grasp your partition setup.
What dose this show:
```
sudo blkid /dev/sda2
```

---

### Post by deadflowr on 2017-01-19
> **scriber said:**
> Thank you for teaching me to use code tags, I do appreciate it !

So what do I do to enable the swap partition that's there but apparently not being used ?

Well, you would actually need to have a swap partition to be able to use it.
That said, I see [s]3[/s] 4 options:

1)resize a partition and make the new space the swap partition, then edit fstab to reflect the new uuid for the swap partition.
The blkid output shows one thing, but maybe parted can show us more:
```
sudo parted -l
```

2)create a swap file and then, again, edit the fstab to reflect that, too.
This has a section on how to create a swap file:
[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F")

3)install the package swapspace, which will allocate swap space dynamically from your existing space.
```
sudo apt-get install swapspace
```

4)optional, ignore it all together.

ninja'd with good advice to double check blkid

---

### Post by scriber on 2017-01-19
> **1fallen said:**
> 
I agree with ajgreeny I don't seem to grasp your partition setup.
What dose this show:
```
sudo blkid /dev/sda2
```

Nothing happens when I type that, asks for my password and nothing after that.

My first HD has 7 Primary partitions which are handled by the Boot Manager on the first partition.
When I boot up, the boot manager lists all the OS's and I choose which one to boot.
The last 2 partitions are for Ubuntu and the Swap file.
I installed Ubuntu from the ISO, which correctly installed to the 2 partitions I had previously created, one for the OS, the other for the swap file.

---

### Post by scriber on 2017-01-19
> **deadflowr said:**
> 
The blkid output shows one thing, but maybe parted can show us more:
```
sudo parted -l
```



```
Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start  End    Size    Type     File system  Flags
 1      395GB  479GB  83.9GB  primary  ext4         boot 
```

So it appears that Ubuntu is installed correctly to it's partition, but there is a 20GB Swapfile partition that is not showing, even though it was created during the install.

---

### Post by #&amp;thj^% on 2017-01-19
> **scriber said:**
> Nothing happens when I type that, asks for my password and nothing after that.

My first HD has 7 Primary partitions which are handled by the Boot Manager on the first partition.
When I boot up, the boot manager lists all the OS's and I choose which one to boot.
The last 2 partitions are for Ubuntu and the Swap file.
I installed Ubuntu from the ISO, which correctly installed to the 2 partitions I had previously created, one for the OS, the other for the swap file.

Yep No Swap was created then.
deadflowr has given you a good link to add the swap.....or as suggested you could just ignore it all together.

---

### Post by scriber on 2017-01-19
> **1fallen said:**
> Yep No Swap was created then.
deadflowr has given you a good link to add the swap.....or as suggested you could just ignore it all together.

I think I know what is happening now after I posted the info for the Ubuntu Partition.

It doesn't show the the Boot Manager and Windows partitions, which is correct as I am using a Hidden Partition system, where only the currently loaded OS shows.

I suspect that the Swap file Partition is also hidden, and I'll have to set the flag to show it too when Ubuntu loads.

Sorry if I have caused you any confusion, but I was just curious to know what the swap file was doing.

For now I will leave it and ignore it for now until I sort it out.

Thank you for all the replies, I really appreciated it and this is certainly a great Forum !:cool:

---

### Post by HermanAB on 2017-01-20
Note that a swap file is the same speed as a swap partition and much easier to add after the fact.  Read the swapon man page - it is all described nicely in there.

---

### Post by scriber on 2017-01-20
> **HermanAB said:**
> Note that a swap file is the same speed as a swap partition and much easier to add after the fact.  Read the swapon man page - it is all described nicely in there.

Thanks again, I did take note in your first post, I plan on getting to it this weekend, time permitting.

---

### Post by scriber on 2017-01-20
Well it is finally solved and working !

I had to edit my Boot Manager settings for the Ubuntu partition and select the space below the pane the Ubuntu partition shows, select  Fill  and select the swap file partition. This made it  visible to the OS

Probably makes no sense to anyone here but that was the solution.

---

### Post by #&amp;thj^% on 2017-01-20
> **scriber said:**
> Well it is finally solved and working !

I had to edit my Boot Manager settings for the Ubuntu partition and select the space below the pane the Ubuntu partition shows, select  Fill  and select the swap file partition. This made it  visible to the OS

Probably makes no sense to anyone here but that was the solution.
Now it makes perfect sense....this was the part I could not grasp from your partitions that were shown previously.
Glad to hear this though.;)
Kind Regards

---

