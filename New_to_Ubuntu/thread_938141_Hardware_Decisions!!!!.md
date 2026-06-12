---
title: "Hardware Decisions!!!!"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by tictac232434 on 2008-10-04
Yes I have been having many problems with my Dell Computer and Ubuntu one of which is probably because it is an older Dell. Everything just seemed to go wrong and but yet I still love Ubuntu and would like to still have it. 

I recently just got a new HP Pavilion dv2000 series notebook. It just came out. Here are the hardware specs.

Hardware

CPU: AMD Turion 64 X2 Mobile Technology TL-60 and 512kb+512kb L2 cache (2.0 GHz)

Hard Drive: 320 GB (ATA?) (System is 64-bit)

Graphics Card: nVidia Geforce 7150M with shared graphics memory

RAM: 4GB's

Now my 320 GB hard drive is partitioned for a 12gb recover drive or what ever. I was planning on making 10 for Ubuntu and 2 for swap or something like that. Please leave your input on the subject because I am deciding if it is even worth getting rid of the recovery drive for Windows Vista and I do plan on keeping Vista in case I do have a problem with Ubuntu I still have an OS to fall back on. (I already have recovery disc's made for Vista and they seem to work. So the drive is a what if kind of thing.) 

THANKS!!!!!!!!!!!

---

### Post by Paqman on 2008-10-04
Definitely keep your Vista recovery partition, you've got a big disk. If you want to use hibernation, you'll need your swap to be the same size as your RAM. Otherwise 2Gb is fine (in fact 1Gb or less would probably do you)

Since you've already got 2 partitions (recovery and NTFS for Vista), you'll end up hitting the max 4 partitions limit when you install Ubuntu (two new partitions: swap and root) This would stop you from ever creating any more partitions, which could be annoying in the future.

The way around that is to create an extended partition which can house other partitions nested inside it, beating the 4 partition rule. I'd put Ubuntu's root parition inside it and leave the swap outside, but that's just me.

You'd have to do this manually though, the automated partitioner in the Ubuntu installer can't do this.

---

### Post by tictac232434 on 2008-10-04
Ok, thank you I will try this.

---

### Post by tictac232434 on 2008-10-06
Worked out great now "Resolved".

---

