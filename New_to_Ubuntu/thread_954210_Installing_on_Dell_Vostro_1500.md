---
title: "Installing on Dell Vostro 1500"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by antipuls3 on 2008-10-20
I'd love to install and experiment with/start using Ubuntu.

Here's my specs:

Core 2 Duo 1.6ghz
2 GBs RAM
160 HD
My sound card's by Sigmatel... are there drivers available? Vista's giving me a hard time, not telling me what the exact model is...
Nvidia Geforce 8600 mGT 256mb.

Any other information I need?

I'd love to get this going... Thanks!

---

### Post by Bucky Ball on 2008-10-21
Don't think you are going to have too many issues. That sound card seems to work fine with Hardy. Nvidia restricted should be ready to load once you hit the desktop. :)

If you want to ease into it you can dual boot with Windoze. If you're looking at a clean install, cool. There are a lot of guides out there in cyberspace and people on the forums.

Remember to post with any issues. If it is something specific, open a new thread and post with a descriptive title. Keep the machine specs and make and model (unless you built it yourself, of course).

---

### Post by antipuls3 on 2008-10-21
I want to dual boot, so I'll get about the whole partitioning thing. I'd love to be fully Linux, 'cause that'd be amazing, but I want to play games to. So I'm open to experimentation. I'm a noob for sure, but I'm trying to be a quick-learning, fast-thinking and all around un-nooblike noob, so I can learn this stuff =)

---

### Post by antipuls3 on 2008-10-21
How much space should I give to Ubuntu?

---

### Post by Bucky Ball on 2008-10-21
> **antipuls3 said:**
> I want to dual boot, so I'll get about the whole partitioning thing. I'd love to be fully Linux, 'cause that'd be amazing, but I want to play games to. So I'm open to experimentation. I'm a noob for sure, but I'm trying to be a quick-learning, fast-thinking and all around un-nooblike noob, so I can learn this stuff =)

I like your enthusiasm! But first, get a glass or cup of your favourite beverage, a piece of paper and a pen. Figure out what partitions you might want spread over the hard drive space at your disposal. Is Windoze installed already or are you starting with a clean slate? Take this into consideration, naturally.

Ubuntu can go on another partition on the same drive as Windoze or on another hard drive altogether.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

That is a cool guide for dual booting. 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fa94dae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3814    30630880+   7  HPFS/NTFS
/dev/sda2            3815        9729    47512237+   5  Extended
/dev/sda5            9365        9729     2931862+  82  Linux swap / Solaris
/dev/sda6            3815        5029     9759424+  83  Linux
/dev/sda7            6246        9363    25045303+  83  Linux
/dev/sda8            5030        6245     9767488+   b  W95 FAT32
```This is my setup. I have Vista on sda1, Ubuntu and an EXT3 big storage on the sda6 and 7 and a FAT32 partition which Windoze uses for my personal data and which can also be read by Ubuntu. sda5 is the Ubuntu swap (2 x your ram). I have no personal data on Windoze partition so I can just kill it and reinstall if I have/want to without needing to pick out my valuables.

For Ubuntu:

/
/home
/swap

are the three basic partitions but there is no reason you couldn't have:

/
/boot
/home
/pics
/vids
/music
/swap

or whatever you fancy. You will get the chance to partition manually during the Ubuntu install. Install windoze first if you haven't already then that drive/partition will show in the installer as NTFS and you know not to go near those ones.

```

skulker@HPLappy:~$ sudo blkid
/dev/sda1: UUID="FC42EAD442EA9326" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="653d41d1-f3d8-4e3c-8fdd-a298084b754c" 
/dev/sda6: UUID="36bd7710-ca84-48c9-9011-e96d336ba192" TYPE="ext3" 
/dev/sda7: UUID="4317640b-79fe-4ee4-a761-84f84991256e" SEC_TYPE="ext2" TYPE="ext3" LABEL="bigboy" 
/dev/sda8: UUID="4893-E3A6" TYPE="vfat" LABEL="FATSO" 
```Good luck, document what you do to help you remember the basics as you are learning, post again if you have problems and welcome to Ubuntu and the forums. \\:D/

---

