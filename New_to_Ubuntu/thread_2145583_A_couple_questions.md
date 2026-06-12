---
title: "A couple questions"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by SilentNite17 on 2013-05-15
Hey guys! I am building a new computer! But, I am running on a really low budget (less than $500) so I can't really afford a normal OS. So that's why I settled on Ubuntu. But I wanted to clarify a few things before I install it for good on my computer. Thanks for your help guys!

1. Is this backwards installable?

Let me clarify that. I noticed that if you already have another OS (I think Windows works) installed on your computer, you can run Ubuntu along the other OS. My question is, can you do that backwards? Meaning, can you install Ubuntu, then once I get enough money for an OS, can I install it alongside Ubuntu?

2. Is it really true that there isn't that much stuff you can do on Linux?

I know that there aren't that many things that are downloadable for Linux. But I would like to know how much there really is that you can't do. Like, game and software wise. 

3. Can I burn to a CD instead of a DVD?

And if so, is there a specific software I should use? If you could point me toward a very in depth tutorial, that would be great. 


Thanks a lot guys! I'll probably remember something I've forgotten later. I'll tell you if I remember. Thanks!

-Silent (Nick)

---

### Post by fantab on 2013-05-15
Welcome to ubuntu!

The answer to your first question is, "Yes, you can install Windows later, if its Windows you are asking about.

Secondly, there isn't anything that you can't do with Linux/Ubuntu, so the answer to your second question is, 'Not True'. There are Games and Software Applications that are made only for Windows and/or Mac, such software may or may not run on Ubuntu/Linux. [WINE]("http://www.winehq.org/") is capable to running 'some' applications and games but not 'everything' Windows. You can check the [WINE DATABASE]("http://appdb.winehq.org/") to learn what works and what doesn't. 
Another thing, in Ubuntu you install software from specified "[Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")" only. There are many [Linux Alternatives]("http://linuxappfinder.com/alternatives") to almost everything you can do in Windows.

Thirdly, 'NO' you cannot use CD because the Ubuntu.iso image is more than the normal CD size, so it won't fit on a CD. You have to use either DVD or USB. You can find "HOW TO" instructions on: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop).

Lastly, [**Linux is NOT Windows**]("http://linux.oneandoneis2.org/LNW.htm").

There are other considerations to bear in mind before you install Ubuntu, if you intend to install Windows later. You can look up for terms like, DUAL-BOOT, UEFI, GPT on this forum or on www for more info. Tell us more about:
* What OS do you intend to install after Ubuntu, Win7 or Win8 or Mac?
* Your computer internals, like CPU, RAM Graphics etc.?

We will help you further once we get that info.

---

### Post by SilentNite17 on 2013-05-15
Thanks a lot for your help! I'm not running anything special. I'm using an AMD A3+ processor (Zambezi), and I would plan on installing either Win7 or 8 (most likely 8). I would have 8G of RAM, and probably not a whole lot of graphics power. Just 128 CUDA cores at max. probably more around 90 something. Here are the full specs for the computer I would be building:

Motherboard: BIOSTAR A880GZ AM3+ Micro-ATX
Power Supply: Rosewill Stallion RDD450-2-SB 450W
CPU: AMD FX-4100 Zambezi 3.6GHz (3.86GHz Turbo) AM3+ Socket Quad Core Processor
RAM: G.SKILL Ripjaws X Series 8G (2x4G) DDR3 240-pin SDRAM 
Hard Drive Seagate Barracuda 1TB 7200 RPM SATA 6.0Gb/s
Graphics: MSI N630GT-MD4GD3 GeForce GT 630 4GB 128-bit DDR3 PCI Express 

There you go.

---

### Post by fantab on 2013-05-15
If you'll let me advice you then I'd say go with WINDOWS 7. The Ubuntu install will be simple, however, you have to decide upfront if you want UEFI or Legacy Boot. If you want to use UEFI boot then you have to partition your HDD with GPT-table. If not then our good old 'msdos-table' will do. Do some reading and you'll know the difference between the two. If you'd ask me then, either is fine for now but UEFI_GPT is the future.

---

### Post by oldfred on 2013-05-16
A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)


 Windows is not Linux
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) 
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
Thread with discussion Sept 2012
[http://ubuntuforums.org/showthread.php?t=2051228](http://ubuntuforums.org/showthread.php?t=2051228)

If you are planning on installing Windows later you do have to plan ahead. 
Windows only installs to primary partitions if BIOS booting and MBR partitions. And you only have 4 primary partitions.
Windows only boots from gpt partitioned drives with UEFI and has very specific partition requirements. But you do not have any issues on number of primary partitions. It only install in UEFI mode from flash drives and depending on version may have do add the UEFI capability. 

Both Windows & Ubuntu will boot from new UEFI/BIOS dual mode system and how install flash drive is booted is how it installs. So boot in BIOS, install will be BIOS. Boot in UEFI mode and install will be UEFI.

If dual booting both installs have to be UEFI or both BIOS.

---

### Post by 3rdalbum on 2013-05-16
Just to correct something you said in your first post. Ubuntu is a "normal OS" for literally millions of people, many of whom also have Windows or can afford to buy Windows.

Ubuntu isn't just what you use when you can't afford Windows. It is what people actively choose when they don't like Windows.

Ubuntu is very different to Windows but if you are open to change you may end off preferring it, and only use Windows for games and use Ubuntu for everything else.

Ubuntu doesn't run Windows software, but there are programs to suit most needs.

---

### Post by 3rdalbum on 2013-05-16
You can install Ubuntu on your system, then when you want Windows you can downsize the Ubuntu partition and install Windows into the free space.

After doing that, you will temporarily lose access to Ubuntu until you run the Boot Repair utility from the Ubuntu DVD.

---

### Post by HermanAB on 2013-05-16
Welcome to Linux.  Enjoy the ride.

BTW, there are a few billion more Linux systems in the world than Windows systems.  Windows sells at a rate of about 100 million per quarter, while Linux devices are produced at a rate of 100 million per month.  You do the math for a typical 5 year lifetime...

---

### Post by Reggy on 2013-05-16
>  1. Is this backwards installable?  Let me clarify that. I noticed that if you already have another OS (I think Windows works) installed on your computer, you can run Ubuntu along the other OS. My question is, can you do that backwards? Meaning, can you install Ubuntu, then once I get enough money for an OS, can I install it alongside Ubuntu?  Yes, if your new OS has easy & flexible installation procedure like Linux/BSD where you can specify on which partition you want to install, so that you dont overwrite existing OS partition. You will also need to check the details of the bootloader of your new OS, whether like Linux/BSD it allows to boot all the installed OSes. >  2. Is it really true that there isn't that much stuff you can do on Linux?  I know that there aren't that many things that are downloadable for Linux. But I would like to know how much there really is that you can't do. Like, game and software wise.  I dont know from where you got this misconception. Linux based OSes are free & opensource. They give the user freedom to do anything & everything with the OS, unlike a propreitary OS where everything is restricted. Any free & opensource software or game will run on Linux, as you can always compile it even if they dont provide the binary for your flavor of Linux. Also, there are many propreitary Linux software & games, but they only provide binaries for well-known Linux OSes. Searching on www for your specific need of software or games would be a good idea. >  3. Can I burn to a CD instead of a DVD?  And if so, is there a specific software I should use? If you could point me toward a very in depth tutorial, that would be great.  Yes, depending on the size. Just burn it, no specific software needed.

---

