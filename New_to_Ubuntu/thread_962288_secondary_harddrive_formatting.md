---
title: "secondary harddrive formatting"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Ace of Knaves on 2008-10-29
I've reinstalled Kubuntu and I was thinking of using up my Seagate HDD (which is the second one I have on the machine) as a media storage device, I've mounted it and all, but now here's the problem; I've installed an OS on there before and didn't format it, so here's the million dollar question: how do I format my second harddrive in Kubuntu while the OS is still running on my first HDD without breaking it?

---

### Post by zakirs on 2008-10-29
well can u post the result of 
> sudo fdisk -l

---

### Post by zakirs on 2008-10-29
i couldnt get ur question properly .. u have kubuntu on ur internal drive and another OS on external drive ... ? and now u r on kubuntu ?? right

---

### Post by bumanie on 2008-10-29
You should not have any issues if you use gparted to format the second drive - just unmount it first. As you will not be working on the drive where the operating system is working from.

---

### Post by vanadium on 2008-10-29
Beware this is the Absolute Beginners Forum, so instructions should be sufficiently specific.

I second the opinion of bumanie, that you can (most safely) use gparted from within your running Ubuntu install. However, you will also need to update your /etc/fstab after partitioning, so there the suggestion of zakirs comes in.

1) You can already proceed with the reformatting.
1.1) Install gparted with the following terminal command (or using Synaptic package manager if you prefer). gparted is not by default installed, although it is available in a live session.
```

sudo apt-get install gparted

```
1.2) Start gparted as root user with the command
```

gksudo gparted

```
The advantage of running gparted from within your current system and not from a live session is that there is no chance to damage your system partitions.

1.3) Select your second drive in the drop down to the right.
1.4) Right-click the partition you want to reformat and click "Unmount"
1.5) Right-click the partition you want to reformat and click "Format to " then select "ext3".
1.6) Close gparted when done.

2) In order to help us now to fix your /etc/fstab, post the output of the commands
```

cat /etc/fstab
sudo blkid

```

---

