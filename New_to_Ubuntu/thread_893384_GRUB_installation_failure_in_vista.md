---
title: "GRUB installation failure in vista"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by askhetan on 2008-08-18
I have a hp-vista-laptop having 3gb ram and 232gb hard drive
i partitioned it as 
150gb(primary)(c drive for vista)
20gb(primary)(l drive for linux)
50gb(logical)(i drive for other files)
12gb(primary)(d drive for recovery)

and i wanted to install ubuntu in the 20 gb hard drive so i shut down my system and put the ubuntu cd in it and started it again.
all the process was fine uptill 94 % installation when it showed "failed to install grub boot loader hD(0)" - "this is a fatal error". I have tried this 5 other times with different ubuntu cds but they show he same error all the time and i never get a complete installation

please help

---

### Post by caljohnsmith on 2008-08-18
Just an observation from your setup, but Ubuntu needs at least two partitions: one partition for the main install and a swap partition. From what you wrote you don't have a swap partition it seems. Try setting up a swap partition, in addition to the Ubuntu root partition, when you go through the installer and see if that helps.

---

### Post by askhetan on 2008-08-18
but from what ive known...swap is needed for auxiliary purposes..it isnt really necessary...and more over i have 3 gb ram...thats almost equal to 2/3 of linux...so where else do u think the fault can be....?

---

### Post by caljohnsmith on 2008-08-18
To the best of my knowledge you have to have at least some swap space for Ubuntu. You could do just 1 GB for example, and I think the only disadvantage you will likely see is that you won't be able to hibernate your computer. So if hibernating doesn't matter, you could try using 1 GB.

---

### Post by unutbu on 2008-08-18
There are a number of reports of the GRUB installation failing at 94%, with the error "failed to install grub boot loader":

[http://ubuntuforums.org/showpost.php?p=5587684&postcount=468](http://ubuntuforums.org/showpost.php?p=5587684&postcount=468)
[http://ubuntuforums.org/showthread.php?t=371483](http://ubuntuforums.org/showthread.php?t=371483)
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135)
  Search for "94%". Poster says he solved his problem by selecting Manual Partitioning, and selecting a partition as ext2 rather than ext3 and then setting the mount point to /.

I just don't understand why what the poster said should work. 

caljohnsmith, do you think maybe if askhetan used GParted to format the Linux partition before installing, this would help?

PS. I think it is possible to run a Linux system without a swap partition. Some people use temporary swap files that they turn on and off when needed:
```

dd if=/dev/zero of=/swapfile bs=1024k count=2000
mkswap /swapfile
swapon /swapfile
... do stuff ...
swapoff /swapfile
sudo rm /swapfile

```

---

### Post by caljohnsmith on 2008-08-18
> **unutbu said:**
> There are a number of reports of the GRUB installation failing at 94%, with the error "failed to install grub boot loader":

[http://ubuntuforums.org/showpost.php?p=5587684&postcount=468](http://ubuntuforums.org/showpost.php?p=5587684&postcount=468)
[http://ubuntuforums.org/showthread.php?t=371483](http://ubuntuforums.org/showthread.php?t=371483)
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135)
  Search for "94%". Poster says he solved his problem by selecting Manual Partitioning, and selecting a partition as ext2 rather than ext3 and then setting the mount point to /.

I just don't understand why what the poster said should work. 

I don't understand why that would work either, but if that workaround does the trick, it's better than not being able to install at all. ;) Also, I did a quick search at bugs.launchpad.net just now, and it seems this bug has been reported in numerous variations; but I didn't see any reports of it being officially resolved.
> **unutbu said:**
> 
caljohnsmith, do you think maybe if askhetan used GParted to format the Linux partition before installing, this would help?

Certainly could not hurt, I'm all for it. He just needs to make sure he uses ext2 of course as you pointed out. :)
> **unutbu said:**
> 
PS. I think it is possible to run a Linux system without a swap partition. Some people use temporary swap files that they turn on and off when needed:
```

dd if=/dev/zero of=/swapfile bs=1024k count=2000
mkswap /swapfile
swapon /swapfile
... do stuff ...
swapoff /swapfile
sudo rm /swapfile

```
Thanks for pointing that out, I should have figured there is a relatively easy way around using a swap partition since there are *always* different ways of doing things in Linux. :) My original impression was that askhetan is on the newbie end of the linux experience spectrum, so I wanted to encourage him to go with a "standard" install to possibly minimize his hassles. But I don't doubt the above method could work fine.

---

