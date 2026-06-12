---
title: "How can I change the mount point of a partition to /home"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Kedster on 2008-09-14
OK so  had ubuntu and i wanted to try Mint so I went to install and when i went to partitioner(during the install) I clicked on the partition that has my home on it and I went to change the mount, point but I couldn't (I had to tell it to use the partition  instead of "do not use partition") and then I could change the mount point, so I did then I hit "Ok" and in the summery thing(the graph thing of the partitioner) it had checked format check box. so I went to change it not to format and clicked "Ok" but it didn't change anything. so I told it just to do nothing at the time and continued the install.  

   now I'm looking for a way to change the mount point of my partition with my old home on it(to /home). if it take a re-install I don"t mind but i really want to still use mint, I have a live cd also. i cnat do basic command but not much in the terminal( like I can follow guides or "step by steps") but need hel and specifications to what to do.

PS if u do give me commands to do I'd like to now what they do and stuff so i can comprehend the commands and maybe help my self next time or someone else.

---

### Post by knattlhuber on 2008-09-14
I'm not 100% sure what you are trying to do. If you are trying to move your home directory to a separate partition, these links might be helpful:

[URL="http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"]http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/
[/URL][http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Kedster on 2008-09-14
no i have a partition with my original Home(from my ubuntu install) and I installed linux Mint on top of ubuntu (and kept my home) what i did during the install is above but i couldent select my home partition as my home during the install so in stead i let it put a new home on the same partition of the OS. so now i have a partition with my ubuntu home(just mounted as a drive) and and other partition with linux mint and the new home (with none of my stuff or settings and not on a seperate partition lol) on it so i want to change the ubuntu home partition to be mounted as my acctual home and used like that

---

### Post by Tatty on 2008-09-14
You will need to add a line to your /etc/fstab file to get your home to mount

```
/dev/sda<your partition number> /home           ext3    relatime        0       2
```

---

### Post by Kedster on 2008-09-14
how would i do that like what commands 
the dive #id sda2  and

---

### Post by Tatty on 2008-09-14
First back up your current fstab just in case:
```
sudo cp /etc/fstab /etc/fstab.backup
```

Then open it in an editor as a superuser:
```
gksu gedit /etc/fstab
```

then add the following line to the bottom:

```
/dev/sda2 /home           ext3    relatime        0       2
```

Then simply save and reboot.

---

### Post by Kedster on 2008-09-14
ok so that sorta worked 
when i restart and login it brings me to the new home so i went into gparted a mounted it then logged out and in and it logged me into my old home:) but then if i restart i got to do it all again each time  
so  think my question is 
how can i get it to mount it automatically

---

### Post by unutbu on 2008-09-14
Please post your /etc/fstab, as well as
```


sudo fdisk -l   # This displays your partition table
blkid           # This lists the UUID of your partitions. The info is used in /etc/fstab.
```

---

### Post by Kedster on 2008-09-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=609ed07a-54a7-414a-9b15-5917439032ad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=85a07073-a273-47d6-8bdc-b1ccb501705c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2 /home           ext2    relatime        0       2

---

### Post by Tatty on 2008-09-15
> **Kedster said:**
> ok so that sorta worked 
when i restart and login it brings me to the new home so i went into gparted a mounted it then logged out and in and it logged me into my old home:) but then if i restart i got to do it all again each time  
so  think my question is 
how can i get it to mount it automatically

Im a little confused.  Which bit worked and which bit didnt?


Also can you post the output from the two commands in unutbu's post above?

---

### Post by Kedster on 2008-09-15
ok so tatty adding
 ```
/dev/sda2 /home           ext2    relatime        0       2
```
to /etc/fstab worked sorta, as long as i  log in manually mount that partition and then log out and back it then is perfect the output of those commands are
```
kedster@kedster ~ $ sudo fdisk -l
[sudo] password for kedster: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc329e402

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9437        9729     2353522+  82  Linux swap / Solaris
/dev/sda2            2471        9436    55954395   83  Linux
/dev/sda3   *           1        2470    19840243+  83  Linux

Partition table entries are not in disk order

``` 

```
kedster@kedster ~ $ sudo blkid
/dev/sda1: TYPE="swap" UUID="85a07073-a273-47d6-8bdc-b1ccb501705c" 
/dev/sda2: UUID="0b80fd1f-52b1-430e-bc25-acec47b0adc2" TYPE="ext2" 
/dev/sda3: UUID="609ed07a-54a7-414a-9b15-5917439032ad" TYPE="ext3" 

```
 
edit i see that sda2 doesn't have a boot thing is that the problem ? if that the problem can i just use gparted and manage the flags and ad a boot flag or somethin

---

### Post by unutbu on 2008-09-15
Kedster, you don't need to set the boot flag. Windows uses the flag to identify 
which partition to boot, but GRUB has a more versatile method and doesn't need the boot flag. 

I'm not sure why your fstab did not cause /dev/sda2 to automount at bootup. 

Perhaps try this:
```

sudo cp /etc/fstab /etc/fstab-20080915   # Make a backup copy
gksu gedit /etc/fstab                    # Run gedit as root
```

Replace your fstab with this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=609ed07a-54a7-414a-9b15-5917439032ad / ext3 relatime,errors=remount-ro 0 1
# /dev/sda1
UUID=85a07073-a273-47d6-8bdc-b1ccb501705c none swap sw 0 0
# /dev/sda2
UUID=0b80fd1f-52b1-430e-bc25-acec47b0adc2 /home ext2 relatime,defaults 0 2
/dev/scd0 /media/cdrom0     udf,iso9660     user,noauto,exec,utf8 0 0

```
Save and exit.

In the above fstab, the "defaults" option has been added to the line for /dev/sda2.
"defaults" is shorthand for "rw, suid, dev, exec, auto, nouser, async"
Included in these options is "auto", which is the option used to signal the system to mount the partition at bootup. (For more info see [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131))

Maybe that will do the trick.

Reboot, tell us how it goes.

---

### Post by Kedster on 2008-09-15
ok so i resarted a few time when i wasent able to get to the net for ur answer and well after i did it like 4 time it just does it automaticaly i dont unsderstand what happened 

would running those command u guys told me to get the outputs of have fixed it cuz that might be when it started working

---

### Post by Kedster on 2008-09-15
i think i may no what happended 

at first when i changed the /ect/fstab i put what u said without checking it(this is my fault not urs) and then i went and checked it and it was ext3 and t needed to be ext 2 so i changed it  could that have bean the problem

---

### Post by Tatty on 2008-09-15
> **Kedster said:**
> ok so i resarted a few time when i wasent able to get to the net for ur answer and well after i did it like 4 time it just does it automaticaly i dont unsderstand what happened 

would running those command u guys told me to get the outputs of have fixed it cuz that might be when it started working

Ah well thats good that its working now then.

Those commands you posted the outputs to would not have made it start working, they were just to print out information on your system.

As to why it did not work before, I have no idea - computers can be funny things some times.


The only thing you might want to do is edit your fstab again to change "/dev/sda2"  to :

```
UUID="0b80fd1f-52b1-430e-bc25-acec47b0adc2"
```

This is not essential, but if you ever change where the drives are plugged into your system then the drives may be assigned different names.  Using UUID makes sure the entry is tied to that specific drive.

---

