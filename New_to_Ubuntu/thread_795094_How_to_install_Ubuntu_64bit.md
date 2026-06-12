---
title: "How to install Ubuntu 64bit"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by munkyboy on 2008-05-15
Hello. This is my first post so hello.

Last night I finally took the plunge into Ubuntu I just bought a new PC and thought I'd give it a go. Setting up a dual boot with windows vista.

I got it all sorted really easy. I was surprised how easy it was. and Im impressed with what i see.

However in my haste I installed the 32bit version, And I need the 64bit version as I have 4GB of ram and the 32Bit is only seeing 3.

My question is. Is there any way to upgrade the current o/s or do i need to remove and start again with the 64bit version. If so how do I get rid of the original installation of Ubuntu?

Thanks

---

### Post by philinux on 2008-05-15
Just use the 64bit live cd and install over your existing 32bit. You can leave you home folder/partition alone if you wish.

---

### Post by munkyboy on 2008-05-15
> **philinux said:**
> Just use the 64bit live cd and install over your existing 32bit. You can leave you home folder/partition alone if you wish.

Thanks for the Quick reply.

Thats exactly what i was wondering about what do i do with the partition. So Just reinstall brilliant.

---

### Post by joanindo on 2008-05-15
there's no way to upgrade from 32bit to 64bit since it's different in architecture. u have to do fresh installation.

---

### Post by lazyart on 2008-05-15
You might find that 64 bit won't see all the ram either due to your motherboard.  Pay close attention to how much memory the system recognizes at POST.  If it's not 4096 megs you have an issue in your BIOS, which can usually be fixed by turning on a setting for remapping the memory hole, or DRAM >4GB or something of the like.

---

### Post by munkyboy on 2008-05-15
> **philinux said:**
> Just use the 64bit live cd and install over your existing 32bit. You can leave you home folder/partition alone if you wish.

Okay so Im trying to do this. And I'm not able to do this from ubuntu i have to start fresh from vista. 

At which point it starts from scratch and trys install ubuntu64 when it comes to the partitioning it gets completley confused hangs for about 30 minutes then crashes and scan disk kicks in.

What am i doing wrong? Do i need to remove remove the orginal installation of ubuntu. If so how is that done? Part of me whats to do that just to start from scratch. But i dont know how its possible

---

### Post by stchman on 2008-05-15
> **munkyboy said:**
> Hello. This is my first post so hello.

Last night I finally took the plunge into Ubuntu I just bought a new PC and thought I'd give it a go. Setting up a dual boot with windows vista.

I got it all sorted really easy. I was surprised how easy it was. and Im impressed with what i see.

However in my haste I installed the 32bit version, And I need the 64bit version as I have 4GB of ram and the 32Bit is only seeing 3.

My question is. Is there any way to upgrade the current o/s or do i need to remove and start again with the 64bit version. If so how do I get rid of the original installation of Ubuntu?

Thanks

Boot up with the 64bit LiveCD.

First delete the swap partition and the partition you installed Ubuntu 32 bit on.  Leave this as free space.

When installing tell the installer to use the largest continuous free space.

After that 64 bit will be installed.

There are a few quirks as Java plugin for Firefox won't work.  I have Hardy 64 installed and all works well.  I do notice it is faster than the 32 bit version but uses more memory as the pointers are bigger.

---

### Post by munkyboy on 2008-05-15
Help.

Okay so I deleted the partion tried to install Ubuntu64 again. Again it just hung for ages. 

Now though when i try to boot into vist it says grub error and wont do anything. what do I do? I think ive broke it.

---

