---
title: "Upgrading from 10.10 to 12.04: swap partition help please"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by vogonpoet on 2012-07-28
Hi, I am completely new to Ubuntu, and would like some help:[B]

Short version:[/B]
I want to install 12.04 properly , I don't want to ruin the Dell  Recovery partition, because it seems to do a good job fixing my mess,  and I want to create a /swap partition. Could anyone guide me through  what's important, and what my best approach to installation is? 

**Background:**
Last week I bought a new Dell laptop (Inspiron M5110)  which came with 10.10 pre-installed. I soon found out 10.10 is no  longer supported, and created a live USB stick for 12.04. After booting  into 12.04, I tried to install it over 10.10, but hit an immediate snag:  it wanted me to create a /swap partition, which I thought I succeeded  in doing, but then when the installation finished, reboot failed: I got  the 10.10 boot screen, which just hanged indefinitely.

I tried  booting from the USB stick again, but that didn't work either, so in the  end I used the Dell Recovery software to reset the laptop back to  10.10. This worked perfectly, but then I was back where I started, using  10.10, and with no swap partition.

Three days ago the sound just  stopped working for no real reason, so I tried booting with the live  USB stick, and got some missing driver message relating to Unity. In the  end I ran the Dell Recovery again, and recreated my USB stick, and now I  am using 12.04 from the USB, no problems.

How to proceed with upgrading to 12.04?

System specs:
AMD A8-3500M APU with Radeon(tm) HD Graphics × 4 
4 GB RAM

As  I said, this computer is new, so I can do a clean install if thats  best. I hope someone can help, because I have been wanting to get into  Linux for ages now - my only other UNIX experience is with an IBM Model  80 which runs XENIX, which I still have use at work on an everyday  basis, but I mainly just try to avoid messing it up, and I kinda hope  Ubuntu is a bit more user friendly :)

**Partition Confusion**
I just had a look at my partitions using GParted, and it seems the swap partition is still there, but I have no idea if its set up correctly. See the picture attached.

OK, sorry this is so long, I will stop now and hope someone can help.
Thanks,
vp.

---

### Post by C.S.Cameron on 2012-07-28
I recently upgraded my wife's computer from 10.10 to 12.04 doing upgrades with Update Manager, it took about 4 days but was educational.
If you run the installer, from the Live USB, it should set up swap space for you, as long as you don't use manual partitioning.

Edit:
Oops, I see you need to use manual partitioning to keep the two Dell partitions, so sda3 should be formatted ext4 for /. The installer should find the swap partition.

---

### Post by ub07 on 2012-07-28
If it had a working 10.10 installed, it does not surprise me that you have a swap partition. What is more surprising to me is why your Windows partition is FAT32 and not NTFS. What is the 4.40 GB ext partition? Is this the one that you created when you thought you were creating a swap partition?

If I were you, I'd try installing again but choose to manually partition your hard drive. You should be able to use those same partitions.

---

### Post by vogonpoet on 2012-07-29
Huh, I was 99 percent certain that the machine did not have a swap partition to begin with. Anyway, is the swap partition sda5 meant to look like that? - I don't understand why its a mounted as a logical partition on sda4 rather than just having primary partition sda4 defined as the swap partition - what is the role of sda4 currently?

I also have no idea what is going on in sda2, because as far as I am aware I don't have a windows install on this laptop, so  whats taking up 1.17 GB of space? Could it  also be part of the Dell recovery setup?

Anyway, I should be aiming to install 12.04 on sda3 right? Is it worth while to create seperate root and /home partitions, or is that not really necessary?

---

