---
title: "older hw won't recognize hard drive"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by P86 on 2008-11-17
Hey everyone, I have a Asus P3B-F motherboard that won't correctly see my 160GB Seagate hard drive. In the BIOS, the mobo sees the drive as an 85GB drive (I have the latest BIOS and have tried to enter the cyl/heads in manually). I booted the computer into Ubuntu using a live CD I had around, and gparted sees the drive as 149GB (which I suppose is the "real" space available).

My question is: is this fine? Maybe I'm just too used to Windoze, which would probably have an issue with this setup. I have a PCI IDE adaptor I could use, but do I have any reason too?

---

### Post by cwsnyder on 2008-11-17
In answer to your second question: Your PCI IDE adapter may not change the BIOS settings, depending on the particular adapter.

The 149G reading is 149*1024*1024*1024.  The 160G reading on the drive is usually something like 160,000,000,000, as you noticed there _is_ a difference.

There are probably BIOS extensions and greater support of the HD under Ubuntu, which is why Gparted can see all of the drive.  You should be fine partitioning, formatting and using the drive under Ubuntu.

---

### Post by P86 on 2008-11-17
> **cwsnyder said:**
> The 149G reading is 149*1024*1024*1024.  The 160G reading on the drive is usually something like 160,000,000,000, as you noticed there _is_ a difference.


Do you think that is normal, or am I losing space on this drive? I know when you actually go to partition a drive, the space available is always less than what is written on the drive. However, 11GB seems a lot smaller

---

### Post by P86 on 2008-11-17
I did some Googling and figured out 149GB is normal for a "160" GB drive. If anyone has any other input/comments regarding using larger hard drives on old hardware, I'd appreicate it. Thanks.

---

### Post by psusi on 2008-11-17
> **P86 said:**
> Do you think that is normal, or am I losing space on this drive? I know when you actually go to partition a drive, the space available is always less than what is written on the drive. However, 11GB seems a lot smaller

What is 149 * 1024 * 1024 * 1024?  It's pretty close to 160 billion.  The hard drive manufacturer's marketing people define a gigabyte as a billion bytes to make the drive look bigger.  In computer science, a kilobyte is 1024 bytes, a megabyte is 1024 kb, and a gigabyte is 1024 mb.

Try setting your bios to auto detect the drive, and enable LARGE or LBA mode to see if it will recognize the whole thing.  If it won't, then you need to make sure that grub is installed in the lower part of the disk that the bios recognizes.  The best way to do this is to make a 100-150 mb or so partition for /boot at the start of the disk.  If you just use one big partition for the whole disk, then grub may or may not land in the part of the disk where the bios can't read it and you won't be able to boot.

---

### Post by cariboo on 2008-11-17
I've used larger drives than the bios can detect for years, you shouldn't have any problems using the drive. 149Mb is normal fo a formatted 160Gb drive, Remember you are losing 5% of the disk to reserved blocks for root, thats 8Gb right off the top, then consider that the HDD manufacturers measure hard drive size differently from the OS and 149Gb is about right.

Jim

---

### Post by egalvan on 2008-11-17
> **P86 said:**
> 

My question is: is this fine? Maybe I'm just too used to Windoze, which would probably have an issue with this setup. I have a PCI IDE adaptor I could use, but do I have any reason too?

It depends on the exact model of the PCI adapter.

Some will allow you to use the latest PATA drives on an older mobo.

You want to use one that is ATA/100 at the least,
ATA/133 is far preferable.
And remember to use 80-WIRE cables.
You lose speed using the older 40-WIRE cables.

I have used PCI adapters to run larger drives on mobo's that would not 'see' the newer drives.

Also, you can partition the larger hard drive into smaller units which can be used. Something else I have done.
/boot is set to 1gig, a swap at 2g (set to approx 2xram) then / is set to 10gig, then /home uses the rest.


Be aware that GRUB has limits, it uses some BIOS code.

And once GRUB hands off to Linux, there is no further limit.

But try it out, see if it works, you have nothing to lose but some time,
 and you will gain a better understanding of your machine and it's capabiliies.

Have fun.

ErnestG

---

### Post by P86 on 2008-11-19
> **cariboo907 said:**
> I've used larger drives than the bios can detect for years, you shouldn't have any problems using the drive. 149Mb is normal fo a formatted 160Gb drive, Remember you are losing 5% of the disk to reserved blocks for root, thats 8Gb right off the top, then consider that the HDD manufacturers measure hard drive size differently from the OS and 149Gb is about right.

Jim

Great, this is what I wanted to hear. Someone who has used this setup without problems. This is obviously one of the ways Linux is superior to Windoze (there are other weaknesses, but that is for a different post ;) ) . Thanks everyone.

---

### Post by psusi on 2008-11-19
> **P86 said:**
> Great, this is what I wanted to hear. Someone who has used this setup without problems. This is obviously one of the ways Linux is superior to Windoze (there are other weaknesses, but that is for a different post ;) ) . Thanks everyone.

The only difference between linux and windows in this area is that with linux you can install grub to a tiny partition in the part of the disk that the bios can see and the rest of the system to the rest of the disk.  With windows you need to install all of windows to a partition that is entirely contained in the part the bios can see, or you risk not being able to boot after an update.

Come to think of it, I suppose you could hack a windows setup to have the boot loader on a small partition in the bios accessible part of the disk.

---

