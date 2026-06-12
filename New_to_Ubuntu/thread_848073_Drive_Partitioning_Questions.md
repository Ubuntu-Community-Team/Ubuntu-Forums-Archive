---
title: "Drive Partitioning Questions"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Helical on 2008-07-03
Hello, I just bought a new laptop I'm planning on installing Ubuntu (never used Linux before) on it when I get it. I also want to leave Vista on it. 

This is the install method I plan on using: [http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

I have a few questions:

1. When I partition my hard drive, will I ever be able to add to my Windows partition later or am I stuck with whatever size I choose from beginning?

2. If I ever decide to add a second HDD is there an easy way to copy the Ubuntu OS + Files over to the other hard drive so I could have a dedicated HDD for both OS's? Would it be a simple process of just copying and then deleting the partitions in each respective hard drive? 

3. With the method lined up in that link would I be able to partition like this: [Vista] [Linux Files] [Ubuntu OS] [Swap]? I assume I would have to click manual instead of guided to do this? I'd like to do this so I can easily uninstall Ubuntu in the event that I want to try different distributions and still keep all my files on my HDD.

4. And is the swap partition necessary since my new system will have 4GB of RAM?

[I don't really know *technically* what a partition is (thus my questions of what can be done with them) - does the computer see it as just a large file?]

Sorry for all the newbie questions. Thanks for any and all help, I look forward to joining the community!

---

### Post by hyper_ch on 2008-07-03
> **Helical said:**
> 1. When I partition my hard drive, will I ever be able to add to my Windows partition later or am I stuck with whatever size I choose from beginning?
You can resize partitions later on but it is tedious and there's always a risk of borking up and lose the data... also you have to consider that windows normally requires the frist partition (as primary partition) and you can only have up to 4 primary partitions.... so if you plan to install windows later on onto that drive, then make an empty primary partition now into which you can later install it.

> **Helical said:**
> 2. If I ever decide to add a second HDD is there an easy way to copy the Ubuntu OS + Files over to the other hard drive so I could have a dedicated HDD for both OS's? Would it be a simple process of just copying and then deleting the partitions in each respective hard drive?
You can do that... but if you want to add a second HDD then I would make the second hdd as primary one, install windows there and then re-install grub...

> **Helical said:**
> 3. With the method lined up in that link would I be able to partition like this: [Vista] [Linux Files] [Ubuntu OS] [Swap]? I assume I would have to click manual instead of guided to do this? I'd like to do this so I can easily uninstall Ubuntu in the event that I want to try different distributions and still keep all my files on my HDD.
Yes, you have to manually do that... the manual installation routine isn't really complicated... I'm just about to make a howto (but more because of encryption) that covers most of that also...

> **Helical said:**
> 4. And is the swap partition necessary since my new system will have 4GB of RAM?
If you want to sleep or hibernate then you need a swap partition that's at least equal in sice.

> **Helical said:**
> [I don't really know *technically* what a partition is (thus my questions of what can be done with them) - does the computer see it as just a large file?]
A partition is a part of the harddisk that has some boundaries and onto which a filesystem can be employed. Windows uses ntfs as filesystem, linux (mostly) ext3, swap is another filesystem... you basically split one harddisk up into sever smaller chunks ;)

---

### Post by Helical on 2008-07-03
Interesting! Thank you very much for the prompt reply, you answered all of my questions (for now :)).

---

### Post by kansasnoob on 2008-07-03
Check out this guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

NOTE: I would personally never use anything but Vista's own tools for resizing the Vista partition!

I'd give Ubuntu at least 10GB to reside in, more is fine. One typo I noticed in the guide is where (on page 3) it says, "Manual - use the largest continuous free space" .......... that should be, "Guided - use the largest continuous free space". Using that method eliminates all the guess work. The installer will create the proper SWAP and everything requiring no decisions or thought whatsoever.

You'll note that on the final page of that guide it says, "If you want to use the GRUB bootloader then you don't need to do anything further. Ubuntu installs GRUB into the MBR by default and will happily dualboot itself and Vista." ............. and that's just what I'd do! But keep the tutorial handy so if you decide to dump Ubuntu you'll know how to restore the Vista Bootloader.

As far as using an external hard drive my personal preference is to keep all operating systems on the system drive and use external drives for data storage.

---

