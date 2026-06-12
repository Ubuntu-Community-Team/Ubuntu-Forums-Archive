---
title: "LVM says volume is full but is not"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by luisjone on 2012-11-08
Hi guys,

Relatively new to Ubuntu and new around here. Few weeks ago I set up a Ubuntu server at home as a LAMP/Media server. Post here as I'm sure must be quite trivial, but for the life of me after couple of days trying and searching cannot find anything....No much installed on the server, no GUI, LVM2, SSH, Webmin, Virtual box (with three machines, one with LAMP, one with Media server and one to play).

At the moment I wanted to test on how to run it from a USB, as I'm waiting for a hard drive and I would like to keep the USB as a backup. And its been great (Other than slow network access, around 10Mg/s). But there is the swap LV (logical volumen) in the USB that wanted to either get rid of or move it to one of my spinning data drives.

I "umount"'ed the swap lv and add it to the root lv. Then unmounted one of the drives(sdb1) and free 6GB. But when I try to create a new lv through Webmin it gives me the error:

> 

**Failed to save logical volume : **

  Insufficient free space: 1536 extents needed, but only 0 availableI repeaded the operation to make sure I had space for whatever reason and get the same thing. Then I tried with the [lvcreate,]("https://wiki.archlinux.org/index.php/LVM") but it would say:

>   Physical volume /dev/sdb1 not allocatable
  No specified PVs have space availableThe result of pvdisplay for sdb1 would be:

> 
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               Ivoryserver
  PV Size               931.51 GiB / not usable 536.00 KiB
  Allocatable           NO
  PE Size               4.00 MiB
  Total PE              238467
  Free PE               2947
  Allocated PE          235520
  PV UUID               fClwiS-1WK4-Fkf1-WNQ7-sdpz-fvQ0-s0x6hS
So I indeed do have 2947PE while LVM is saying it needs only 1536. The drive has two ext4 lv file systems and I shrank one of them, so I thought that perhaps have to delete the partition or something not to just shrink it. However I got the exact same procedure perfectly accomplished (as I am describing) it in another drive :confused: . But I would like to do it instead in the sb1 as it is the backup up one and not so heavily used. I should be missing something....Any ideas?

pvs returns:

>  
 /dev/sda1  Ivoryserver lvm2 a-   931.51g     0
  /dev/sdb1  Ivoryserver lvm2 --   931.51g 11.51g
  /dev/sdc5  Ivoryserver lvm2 a-    14.88g     0
Many thanks in advance for any suggestion/comment.

---

### Post by luisjone on 2012-11-10
Ok, I was right, it was something trivial... But in case this might be useful to anyone with the same problem:

I've touch many many things during days without perfectly knowing the effect of each one of them (that's how this kind of problem start...but hey, that's the way to learn) so I cannot tell for sure. But somehow I've found a little bugger in the webmin iterface>logical volume management> physical volume tab> "drive you are having problems with" details> there is a radio check box that reads "Enabled for allocation?" and was set to "No". I do believe changing this bad boy to "Yes" solved the problem.

I don't know how to change this with the command line but there must be a way (I don't even know how this got set to "No" as I did make volumes before the problem). If anyone knows I would love to learn how.

However, in case this is not your problem, I would recommend:

[http://tldp.org/HOWTO/LVM-HOWTO/lvm2faq.html#AEN391](http://tldp.org/HOWTO/LVM-HOWTO/lvm2faq.html#AEN391) 

Cheers to you all.

---

