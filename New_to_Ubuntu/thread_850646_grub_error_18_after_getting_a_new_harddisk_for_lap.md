---
title: "grub error 18 after getting a new harddisk for laptop"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by taekr on 2008-07-05
Hi, 

Wow.. this is really complicated. here it goes. 

Bought a new harddisk and ..    

I partitioned my harddisk into 4.. 

First partition 30GB for WinXP - NTFS 
Second partition 140GB - NTFS 
Third partition 10GB for root - ubuntu hardy 
Fourth partition 70GB for Home - ubuntu hardy 
Fifth partition - Swap 

I installed WinXp first then.. installed ubuntu.. and I'm getting Grub error 18. 

After long research, I have found that my laptop doesn't support harddisk bigger than 130GB or something. So if my boot information is installed out of range where the bios can not reach, then grub error 18 happens... 

From the GRUB Manual:
18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general


I also found some solutions...  such as 

try to put the kernel as close to the first (in BIOS) hard disk MBR as possible (kernel is in the /boot directory, so you can make a separate dedicated boot directory or put the entire Linux closer, like right next to your Windows).


Well, the real problem is I understand the theory... but how do I do it?? it's so complicated..  

Can you please give me step-by-step instructions?  Some says created a small partiiton (500MB) and copy MBR there.. but 1. how to create the partition close to Windows or within the range 2. HOw to copy MBR...     

I have tried to read manuals... oh.. just too much for me T T

Can you help me please?

---

### Post by logos34 on 2008-07-05
> After long research, I have found that my laptop doesn't support harddisk bigger than 130GB or something. So if my boot information is installed out of range where the bios can not reach, then grub error 18 happens...If your sure that's the problem and there's no Bios upgrade to fix it...

Try installing again.  Shrink the first partition, the 30 gb windows, down just a tad, ~100 MB is really all you need for a separate /boot (unless you plan to keep a whole crapload of old kernels).  Create a new primary partition right there, between the two ntfs partitions.  Format it ext3 with mountpoint '/boot'.  Then delete the ubuntu partitions and create a new, extended partition in their place.  Put root, home, and swap inside on logical partitions with mountpoints of '/', '/home' and '/swap', respectively. 

You can also use Gparted (system>admin>partition editor) to partition and format prior to the installation process.

---

