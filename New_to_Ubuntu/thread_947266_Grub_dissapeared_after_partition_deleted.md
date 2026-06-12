---
title: "Grub dissapeared after partition deleted"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Wickd on 2008-10-14
Grub loader disapeared rafter deleting a partition
Hi there

I seem to be having some problems with my Grub bootloader.

Here is what I did:

I had the following partitions
hd0,1 windows (8gb) fat32 (sda1)
hd0,2 ubuntu (18gb) ext3 (sda2)
hd0,3 swap
hd0,4 Files (200gb) fat32 (sda4)

I then proceeded to remove all partitions and enlarging my ubuntu partition to 248 gb and a 1 gb swap, without formatting anything. I use the Ubuntu partitioner on the live cd

When I rebooted grup dissapeared and was replaced by an Intel(r) Boot Agent v1.2.50

I have tried various methods and also studied the Grub Bootloader process and came to the conclusion that maybe the Master Boot Record (MBR) refered to hd0,2 where it has now changed to hd0,1.

Also my Ubuntu still has the Ubuntu partition saved as sda2. So I would like to change the partition name to sda1 and also have the Grub bootloader configured to run instead of the Intel bootloader, since the Intel bootloader is not working at present

Please if you have a solution I would be incredibly happy,since I have been trying to fix this for a week

Thanks in advance

---

### Post by shabs on 2008-10-14
Hi wickd
I'm not sure if this is relevant but on this dual booting tutorial they talk about restoring the grub bootloader: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)
I hope this helps.

cheers.

---

### Post by Ryadt on 2008-10-14
> **Wickd said:**
> Grub loader disapeared rafter deleting a partition
Hi there

I seem to be having some problems with my Grub bootloader.

Here is what I did:

I had the following partitions
hd0,1 windows (8gb) fat32 (sda1)
hd0,2 ubuntu (18gb) ext3 (sda2)
hd0,3 swap
hd0,4 Files (200gb) fat32 (sda4)

I then proceeded to remove all partitions and enlarging my ubuntu partition to 248 gb and a 1 gb swap, without formatting anything. I use the Ubuntu partitioner on the live cd

When I rebooted grup dissapeared and was replaced by an Intel(r) Boot Agent v1.2.50

I have tried various methods and also studied the Grub Bootloader process and came to the conclusion that maybe the Master Boot Record (MBR) refered to hd0,2 where it has now changed to hd0,1.

Also my Ubuntu still has the Ubuntu partition saved as sda2. So I would like to change the partition name to sda1 and also have the Grub bootloader configured to run instead of the Intel bootloader, since the Intel bootloader is not working at present

Please if you have a solution I would be incredibly happy,since I have been trying to fix this for a week

Thanks in advance
Please do not create multiple threads for a single question.
[http://ubuntuforums.org/showthread.php?t=947259](http://ubuntuforums.org/showthread.php?t=947259)
It is against forum's rules.

---

### Post by wjp.reg on 2008-10-14
> **Wickd said:**
> Grub loader disapeared rafter deleting a partition
Hi there

I seem to be having some problems with my Grub bootloader.

Here is what I did:

I had the following partitions
hd0,1 windows (8gb) fat32 (sda1)
hd0,2 ubuntu (18gb) ext3 (sda2)
hd0,3 swap
hd0,4 Files (200gb) fat32 (sda4)

I then proceeded to remove all partitions and enlarging my ubuntu partition to 248 gb and a 1 gb swap, without formatting anything. I use the Ubuntu partitioner on the live cd

When I rebooted grup dissapeared and was replaced by an Intel(r) Boot Agent v1.2.50

I have tried various methods and also studied the Grub Bootloader process and came to the conclusion that maybe the Master Boot Record (MBR) refered to hd0,2 where it has now changed to hd0,1.

Also my Ubuntu still has the Ubuntu partition saved as sda2. So I would like to change the partition name to sda1 and also have the Grub bootloader configured to run instead of the Intel bootloader, since the Intel bootloader is not working at present

Please if you have a solution I would be incredibly happy,since I have been trying to fix this for a week

Thanks in advance

Well if you removed ALL the partitions, ALL would be lost, wouldn't it?  

Does anything boot?

---

### Post by subzero316 on 2008-10-14
> **Wickd said:**
> 

I have tried various methods and also studied the Grub Bootloader process and came to the conclusion that maybe the Master Boot Record (MBR) refered to hd0,2 where it has now changed to hd0,1.


 

How did you come to that conclusion :confused:  My bet is Grub was erased when you resized. Reinstalling grub will work!! if you point out to the proper location what steps did you follow ?

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by Wickd on 2008-10-14
Soz admin, didnt know where to put it. my apologies

No I did not delete all partitions. I left my linux partition in tack, I only resized it using gparted, but have to boot from cd if I want to boot Ubuntu

---

### Post by Wickd on 2008-10-14
> **subzero316 said:**
> How did you come to that conclusion :confused:  My bet is Grub was erased when you resized. Reinstalling grub will work!! if you point out to the proper location what steps did you follow ?

Well I read this tutorial: [http://www.dedoimedo.com/computers/grub.html]("http://www.dedoimedo.com/computers/grub.html") and also a bunch of posts on this forum.

According to the tutorial Grub rewrites the MBR to reference to a position on a partition, so I thought well if I was 'clever' enough to remove my windows partition, except my linux partition, which has the bootloader on, then maybe the reference should change from hd0,1 to hd(0,0) in the MBR? Or maybe I misunderstood something along the line

I am still quite fresh to Ubuntu have been using for about month or so.

Thanks

---

### Post by wjp.reg on 2008-10-14
> **Wickd said:**
> Well I read this tutorial: [http://www.dedoimedo.com/computers/grub.html]("http://www.dedoimedo.com/computers/grub.html") and also a bunch of posts on this forum.

According to the tutorial Grub rewrites the MBR to reference to a position on a partition, so I thought well if I was 'clever' enough to remove my windows partition, except my linux partition, which has the bootloader on, then maybe the reference should change from hd0,1 to hd(0,0) in the MBR? Or maybe I misunderstood something along the line

I am still quite fresh to Ubuntu have been using for about month or so.

Thanks

That being the case you can reinstall grub using the following directions.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

good luck!

---

### Post by Wickd on 2008-10-14
> **wjp.reg said:**
> That being the case you can reinstall grub using the following directions.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

good luck!

I have tried that countless times already. But I do think I might have discovered what the problem is. The stage 1 file still refers to the hd(0,1)

But I do not have that partition anymore. I only have 2 partitions at the very moment. the first being my ext3 and the second my swap. Could this be part of the problem?

Thanks

---

### Post by Wickd on 2008-10-14
Hi guys thanx alot! It finally works. Thank You very much for your help

---

