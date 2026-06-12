---
title: "Boot to previous kernel wiped out Ubuntu!?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-20
Hi,

I have a mistery on my hand.

I am running Ubuntu 13.04 on my laptop but still use 12.04 for some of my work. 12.04 now lives on an external hard drive running kernle 3.9.6. When I need it I just boot from the external hard drive. Yesterday I booted into 12.04 only for a little bit to check for updates (there was none) so I thought maybe I should boot into an old kernel (for no particular reason) so I rebooted, saw the grub screen and chose previous kernel versions and tried to boot into kernel 3.2.0-38 and then it went crazy. It struggled for a long time and showed unknown file system and grub rescue.

So I booted into 13.04 on my laptop (internal hard drive), plugged in the external hd with 12.04 and checked.
 
fdisk -l didn't seem to find anything wrong
```
Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b6bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    41945407    20971680   83  Linux
/dev/sdb2        41947134   564340735   261196801    5  Extended
/dev/sdb5        41947136   325720063   141886464   83  Linux
...

```

sdb is the exrternal drive and sdb1 is / partition for 12.04, sdb5 the /home

But blkid didn't see sdb1 and sdb5. It found all partitions on sdb except sdb1 and sdb5

So I fired up gparted and I saw that both sdb1 and sdb5 had file systems described as "unknown" and they appeared as blank boxes, it seemed that all the data were wiped. Ubuntu 12.04 gone!!  See the screenshot (though I suspect it was not really gone, just somehow not detected)

Fortunately I had cloned the whole system. So no sweat, I just reformatted sdb1 and sdb5 with gparted, ran fsarchiver and less than an hour later I was back in business. I rebooted a few times into kernel 3.9.6 and all worked fine, I  checked for kernel 3.2.0 in synaptic and saw nothing unusual. then I tried to booted into kernel 3.2.0. again and the same thing happened.

So I restored the image again, booted into 3.9.6, open synaptic and removed the kernel 3.2.0-38 with all the headers, rebooted and then installed them again. I noticed that there was a version change though, I couldn't find 3.2.0-38 in synpatic any more, so I installed 3.2.0-49 instead. I tried to boot into 3.2.0 again an this time it worked.

I have restored 12.04 completely so the practical problem is solved, but I really want to know what had happened. Does anyone have an explanation? 
Thanks.

---

### Post by monkeybrain2012 on 2013-06-21
Hi,

Any possible explanation of what happened?

---

### Post by grahammechanical on 2013-06-21
Grub in the MBR will look for its grub.cfg file in /boot/grub on the partition it is being booted into by the set root= setting. Other settings identify the partition by a Universally Unique Identifier (UUID). A long line of alpha-numeric characters. Grub will also look for a linux kernel image and an initrd.img which in your case should have been vmlinuz-3.2.0-38-generic in /boot and initrd.img-3.2.0-38-generic.

If Grub cannot find its way at these corners (and no doubt others) it cries Rescue! It is my guess that the kernel 3.2.0-38 was deleted at some point but you failed to boot into 12.04 and run

```
sudo update-grub
```
```
sudo grub-install /dev/sdb
```

to rewrite grub.cfg. So, you were using an out of date grub menu that pointed to a kernel that did not exist. Did you try to boot into 12.04 from the grub menu in the MBR of the internal disk? If that had been updated recently you may not have seen that 3.2.0-38 kernel to boot into.

My explanation might not be the correct one but I find it convincing :)

Regards.

---

### Post by monkeybrain2012 on 2013-06-21
Hi, thanks for the reply.

When it happened the first time it was not a restored. It has been running since the begining of time so I don't think there should be any grub issue. 

After I restored the first time I did run sudo update-grub when I booted into kernel 3.9.6 before I tried again to boot into grub 3.2.0.

But even if I didn't I should be able to just shut down the machine and reboot into 3.9.6, but I couldn't do that (got the same grub rescue unknown file system error) and grub not detecting the kernel doesn't explain why the partitions is not detected by blkid and appeared to be entirely wiped clean when viewed in gparted when I examined the hard drive from a healthy 13.04 install.

---

### Post by monkeybrain2012 on 2013-06-22
No explanation for my mystery? :)

---

### Post by monkeybrain2012 on 2013-06-24
Bumps. I know it is not a pressing issue as I have restored my OS, but still it bothers me. :)

---

