---
title: "mkfs stuck in Unbuntu Server 12.04"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by mbrothwell on 2014-01-09
Hello everyone. I'm setting up a home media server and I thought it would be a great opportunity to get my feet wet with Linux, so here I am.

I'm running Ubuntu server 12.04 on a Windows 8.1 Pro Hyper-V virtual machine. The Ubuntu installation is on a 10GB partition on the SSD, and I am trying to add a 2.5TB HDD for media storage. The partition spans two drives, which I have made into one partition using windows 8 storage spaces. The virtual HD is a .vhdx file connected to the VM with a virtual SCSI controller.

Im using parted to label and partition the new hard drive, but when I try to create a file system using the following command:

mkfs.ext4 [COLOR=#660033]-E[/COLOR] [COLOR=#007800]lazy_itable_init[/COLOR]=1 /dev/sdb1

I get one line of output: "mke2fs 1.41.9 (22-Aug-2009)" then nothing, it's been sitting at this screen for about 12 hours.

Is this working as intended? Should I be seeing more output or has it frozen?

I've also tried the command without the lazy_itable parameter and it has the same result.

Thanks!

---

### Post by SeijiSensei on 2014-01-09
First, you need to run mkfs as root with sudo  ("sudo mkfs ...").  I'd also suggest adding -v to the options to make the command "verbose."

However I wonder whether drives joined together with a Windows technology will be usable under Linux.  Usually if you want to join together two hard drives in Linux you can either choose [software RAID0 or LVM](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html).  

One command you can try to see what Linux thinks of the device is "badblocks."  Try running

```
sudo badblocks -svn /dev/sdb1
```

It will report its progress as it searches the device.  You can stop it with Ctrl-C.  

If you aren't running Windows on this machine, I would stick to Linux-compatible technologies like RAID or LVM.

---

### Post by mbrothwell on 2014-01-09
Thanks! I'll try this out when I get home. 

I had also considered that Linux might not like the drives joined by Windows. I thought I might delete the windows partition, create two seperate virtual hard drives and mount the hard drives individually in Linux, but I will look into your software RAID0 or LVM suggestion.

---

### Post by mbrothwell on 2014-01-10
I let badblocks run for about 3 hours and it didn't come up with any errors.

So I deleted the windows "storage space" join and the corresponding .vhdx file.

Formatted the 2TB drive in Windows, created a 2TB .vhdx for the vm.

Used an fdisk tutorial (no longer needed gpt because of the size), had the drive partitioned and mounted in 10 minutes. 

mkfs took about 10 seconds! I'm not sure whether my problem was the windows join or I was doing something wrong when using parted, I assume it was the former.

---

