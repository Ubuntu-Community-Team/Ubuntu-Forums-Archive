---
title: "installing ubuntu with windows......."
date: 2008-09-07
forum: New to Ubuntu
---

### Post by sankz.21 on 2008-09-07
hey guys i have tried installing ubuntu on my own..........but i cannot do it............i have windows xp on my hard drive........but i have kept a good 50gb blank for installing ubuntu........please can anyone post a detailed procedure on how to install this ubuntu 8.04 and make my PC a dual operating system......

thank u

---

### Post by Crafty Kisses on 2008-09-07
This link maybe very useful to you: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by sankz.21 on 2008-09-07
bt i want to install ubuntu first.........what about that??????

---

### Post by Sin@Sin-Sacrifice on 2008-09-07
If you mean you want it to boot first or even as the default OS then no worries man. When you install ubuntu it will, by default, install grub and that has ubuntu as the default OS. I was worried about that too and am happy with the results. I actually have to work harder to reboot into windows than installing into wine in most cases.... ha. The only reason I still have windows is because I can't play some of my games on wine.

---

### Post by ad_267 on 2008-09-07
If you already have space set aside for Ubuntu then you probably want to use the manual partition method when installing. You can use gparted from the live CD (System - Administration - Partition Editor) to format the Ubuntu partition as ext3. You also need to make an extended partition which contains a swap partition that is about 2GB or twice the size of your ram, which ever is smaller. I've attached a screenshot to show what my partitions look like with a windows partition.

It is a lot easier to install windows first because then you don't have to worry about the boot loader.

It might be easier to resize your windows partition to take up the whole drive then you can use the Ubuntu installer to resize that partition and fit Ubuntu on there and it will sort out swap and everything automatically.

---

### Post by sankz.21 on 2008-09-07
yeah buddy u are close......thats what i want...what opetions do i exactly select while manual partioning......like which mount point,what size, etc etc.......thats what i wanna know.....can u juss print scress the stuff for me......thank you

---

### Post by ad_267 on 2008-09-07
I'll try and do it from memory so I don't have to load the cd and installer. I find it easiest to first set up the partitions in gparted like I showed in the previous post. That should be pretty straight forward if you already have some free space. Just create new partition that's ext3, then create an extended partition, then create a Linux swap partition in the extended partition.

Then when you select manual partitioning, you set the mount point for your ext3 partition as / and the swap partition doesn't have a mount point. You also need to tick the option to format the ext3 partition. If you want you could also have a separate ext3 partition mounted at /home for all your personal stuff but that isn't required.

There's some information here on this: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

---

### Post by Tatty on 2008-09-07
Try these two links.  The first link should sort you out, but if you need any more detail, the second link is the ubuntu community wiki page on the subject of dual booting

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And as mentioned by Ad_267, It is much easier to install windows first, as windows can get upset if it detects other OS's when you try to install it.

---

