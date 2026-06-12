---
title: "Ubuntu help"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by Mahrio on 2013-03-20
[COLOR=#000000]Hi guys, so heres a little back-story. I dualboot windows 8 and ubuntu 12.10. I use two partition on the same HDD. My ubuntu partition was starting to run low on memory, so i added ten gigs to it. Now it wont boot in to ubuntu, it says: Error no such devie : 7802EDF027EA234. so then i decided to restart my computer and select "Advanced boot options" or the option that's something like that, and i selected the option with "(recovery)" beside it. then a bunch of text came on my screen, i let it do it's thing, then i got the message: Alert! /dev/disk/by-uuid/7802EDF027EA234 does not exist [/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]Dropping to a shell! (ash)

So yeah, you guys have any advice? I'm a complete noob to ubunutu. I read some stuff about grub, and checked my grub folder from windows 8 and it's empty.

So, Boot-repair gave me the link paste.ubuntu.com/5632890

Any and all help appreciated, Thanks guys! :smile:
-Kind Regards[/FONT][/COLOR][/COLOR]

---

### Post by Impavidus on 2013-03-21
So this is windows 8 in legacy/MBR mode (or how is it called precisely) with Ubuntu as wubi install. This is not a true dual boot. Can you still boot windows? How did you enlarge the Ubuntu "partition" (a virtual partition really)? The correct way is described here: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

I see your computer has a 320GB drive with two windows partitions, the second about 280GB, containing your windows installation, the first about 40GB, where wubi is installed inside a windows file. I think you made this partition larger to give Ubuntu more space, but that won't work. You have to make the root.disk file larger, but the limit is 30GB.

As it is clear to me you want more than 30GB for Ubuntu you'll have to move on to a real dual boot. You can use your live cd to make backups of the files you keep in your virtual Ubuntu partition, backup your important windows files as well and install Ubuntu by booting from the live cd. The best course of action may be:
- Make backups;
- Uninstall wubi;
- Delete your partition containing wubi and resize the windows partition if you wish;
- Reboot a couple of times to give windows a chance to run any repairs it like to do;
- Boot from the live disk and install Ubuntu on the free disk space;

I'm slightly worried because your Windows is the second partition now, as I believe Windows prefers living in the first, but it may work. Or wait for advice from people more familiar with the topic than me. Also read the installation instructions: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Oh, your grub directory containing anything useful is located on your virtual Ubuntu partition. Windows can't read that.

---

