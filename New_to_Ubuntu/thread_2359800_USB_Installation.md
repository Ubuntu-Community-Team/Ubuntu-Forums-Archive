---
title: "USB Installation"
date: 2017-04-27
forum: New to Ubuntu
---

### Post by johnny7oak on 2017-04-27
OK... so I have two u.s.b installation flash cards.   I was able to  install one side by side windows 10 and love it.  The other is giving me  difficulty.  For some reason I cannot boot from U.S.B - H.D.D and I  tried to load an ISO with none of the extra features... D.V.D -RW is the  best I got, and it doesn't load Ubuntu 16.x any suggestions?  I was  just going to give up, but I like the thought of having a dual boot  Ubuntu manager on there.  I really like that Ubuntu selects instead of  the old Windows dual boot thing that windows 8.1 and windows 7 had  going.  I kind of felt like Windows 10 hijacked the system, but can't  really say I am alone there.  I still wonder if the u.s.b installation  of windows 10 will even work.  I think it was a windows 8 -> windows  8.1 -> windows 10.  the great thing about that machine is it actually  has office 2017.  I had been using my office 2007 student (cause home  and student apparently gives you three uses).   Anyways, I have been  kicking around the idea of using office 2007 student on a second machine  but thats just back-story/rambling and probably irrelevant.  I like my  libre office.  Again probably irrelevant.

Any suggestions on getting that other computer to boot Ubuntu 16.x &#9786;

---

### Post by cariboo on 2017-04-28
Seeing as it has nothing to do with your post, I removed the html code. We use BBcode here, check out this page:

[https://ubuntuforums.org/misc.php?do=bbcode](https://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by oldfred on 2017-04-28
Is system UEFI or BIOS?

Are you trying to create installer or have you installed and cannot boot?

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by johnny7oak on 2017-04-28
I can't even find the usb device when I select from my boot options...

---

### Post by oldfred on 2017-04-29
Is this installer, or your full install?
UEFI or BIOS?

Full installs in UEFI mode required some extra effort.

---

### Post by johnny7oak on 2017-04-29
Full install, Bios... 
Turn on with USB inserted
&#8594; starts windows 10
&#8594; restart
&#8594; hit boot select 
&#8594; pick USB -HDD
 &#8594; skips past to start windows 10,
&#8594; power off
&#8594; disable primary windows boot hdd.
&#8594; restart
&#8594; gives me the look of nothing but HDD with no OS
&#8594; restart
&#8594; reset bios settings
&#8594; gives me the look of nothing but HDD with no OS

&#8594;try ISO: boot from DVD... nothing
&#9785;

---

### Post by oldfred on 2017-04-29
pick USB -HDD

If it shows that, it may not be correct. My old BIOS system would not boot any USB choices. 
It only only worked with the hard drive choices and flash drive even though in USB port was another hard drive.

Or it could be flash drive not correctly configured.

---

### Post by johnny7oak on 2017-04-30
Explain flash drive not correctly configured?

I've tried all usb ports, is this something the motherboard driver disk would solve?  Its a partial usb 2.0/3.0 motherboard and I assembled the desktop myself... some of it was pieced together from left overs.  I have a ATI Radeon GDDR 3 1 gb video card... about 8 gb ddr3 ram maybe nearing 16 I will check, I have about 16 listed on this machine not sure why... maybe I had 4x 4 gb sticks and there is some parity going on?, 1 dvd-rw, 1 blu-ray dvd-rw combo, 3 HDD - 1 mechanical, 2 ssd (one small ssd), and I have an old tv tuner card so I can turn it on by remote... I wanted a floppy/flash card reader but I kind of think that would be pointless.  I had one but I think the cable broke and I am using the 3'5" slot for one of the hard disks anyways.  thats the specifications... I dropped in my old phenom II quad core cause I couldn't afford a good newer processor.  But I still have my usb 1.0 floppy attachment I had for my laptop... so hey.. as long as that functions i still have my one floppy drive. (1 diskette storage, 1 diskette with driver for 10/100 mbps lan card). I will get my usb 3.0 memory card reader someday.

Note: there is 8 GB over there... I think it was because I had 4x 2 GB of DDR2 1066 transfer in the previous machine and that was okay, but I just matched them on the build with 2 x 4GB 1600 transfer.  Two desktops are better than one... and I thought, well... that will match them well enough. Besides 4 GB sticks never came to DDR2 in the states.  Promised to us, but never came.  I don't mind it so much it was the best transfer rate sticks I could get without over clocking... and they had cool heat sinks.  patriot did some good stuff in heat sinks at the time.  I think they work, but I probably gave them to my Dad... he probably doesn't use them but they are good sticks.  I think it was good move to DDR3 cause thats the parity introduction, if I recall right.  I will wait till the 8 GB (or those terribly expensive 16 GB) sticks get cheap then upgrade to 32 GB on my best machine, and move my two best heat sinked ones over.  Unless I discover the heat sinked ones are the parity ones.  DDR4 has already hit the market, and from what I gather there are a lot of features that ensure data transfer is good.  And they made them 4x transfer so we get like 4 bits of data at once... parallel transfer on each memory transfer.  I still think thats going to be incredibly much like early parallel was for our drives.  I'm avoiding DDR4 when DDR5 hits... maybe then I think about parallel transfer on each transfer of memory modules.  Now make it a hex bit instruction and I understand.  I buy in to hex bit transfer.  The ALU on A 4 bit transfer means you changed hands with some sort of and/or/nor or other ALU operation just to quantify from Hex to binary and split it four ways... probably does this anyways in most of the interaction of OS, but memory stored in Hex would be simple compared to 4x transfer of binary registry.  I worked in HEX for 8085 use of I/O logic in microprocessors 1 and 2... It was the basis for my final project for my associates in my major of Electronics Technician.  We had sound output, LED segment Display, LED's, toggle switches, and keypad entry.  My last program was a prompt I devised that would use the characters on that 8 segment LED display to ask for 5 or 6 characters to Marquette across.  Its very very difficult to get the segment characters but you still had to "entr" the characters available... I was also looking at limited eprom for the OS and the other 6 programs stored in the memory registry.  I would have loved to done more characters and maybe utilized the toggle switches to alter the flow of the Marquette.  The switches would have just needed to be set to vary the time delay between segments.

---

### Post by oldfred on 2017-04-30
I do not know AMD, they are changing drivers.
But you probably need no modeset.

If Windows is hibernated then that can cause issues.
If RAM not good, Linux has more issues than Windows. Windows will boot with bad RAM, and just cause unknown issues later on.

Are you trying to boot a hard drive entry. Ignore all USB choices. My old Gigabyte board had many USB entries and none worked. And I knew it was a good flash drive as it booted my laptop. But then one day with flash drive plugged in, I rebooted and under hard drives was the flash drive.

       Trying AMDGPU-PRO 17.10 On Ubuntu 17.04 (does not work directly)
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04)
[https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

---

### Post by johnny7oak on 2017-04-30
I will try a hard drive boot.  It is a Gigabyte board.  The problem may be finding the Hard disk.  I have 3 HDD attached as it is.  If I cannot detect it as a Hard disk, do you have any suggestions? I know the memory is listed as good enough for windows 10.  The parity may be in affect on this machine which has 4 x 4GB PC1600 memory modules and lists only 15.6 GB of memory.  I can do a memory check.  I should find that under administrative tools anyways.  I haven't done that on windows 10 yet.  Might be good to explore that utility for changes.  I actually think the last I did it was with windows 7 or 8.1.  Still any suggestions with a gigabyte board and multiple drives for BIOS boot selection?  maybe keep booting and booting till it detects it, obviously 3 disks is a lot... so I will have to disable a drive.  I want to ssd raid the disks but I have data on them.  If they are blank I am totally going to do it.  If its my OS on a SSD no way... I love to put my OS on a SSD.  the other SSD is kind of small, so I know its either the large one or the mechanical drive. type 0 of course... I don't have the money to mirror.

---

### Post by oldfred on 2017-04-30
What model Gigabyte board?
It was a Gigabyte BIOS only board that I had. It had many USB boot entries, none useful. Flash drive was always under hard drive boot choices.
But flash drive has to be correctly configured to be bootable.
Which installer did you use?
       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

       Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)
Gigabyte H170
[URL="http://ubuntuforums.org/showthread.php?t=2312650"]http://ubuntuforums.org/showthread.php?t=2312650

[/URL]
 Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to AMD  boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[ 

[URL="http://ubuntuforums.org/showthread.php?t=2312650"]
[/URL]

---

### Post by johnny7oak on 2017-05-01
I will try looking to enable IOMMU in the BIOS...

it is an AMD board.  Its a GA-78LMT-USB3

is there any problem with using the same USB boot stick?  I have two but I cannot remember which is which.  I was going to give one to my brother.


UPDATE:  I AM GOING TO CLOSE THIS THREAD.  Its something to do with that BIOS Chip.  I am having issues with it... crashing in the bios settings.  I might need to pursue gigabyte's forums.

---

