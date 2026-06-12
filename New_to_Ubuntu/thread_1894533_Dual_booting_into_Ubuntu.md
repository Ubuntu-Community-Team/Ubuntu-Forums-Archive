---
title: "Dual booting into Ubuntu"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by willythecat on 2011-12-12
AMD Athlon ll X2 250, Windows XP Home SP3 (32-bit), 4gb ram, partitioned C drive (C/D) and an F drive.
Hello everyone,
Have JUST downloaded Ubuntu 11.10 (64-bit) using "wubi"(?) onto my D drive and now have dual boot. 
Everything worked fine first time, but boy is it different! Having used XP for years, will certainly have to practice on this new OS! Looks good though.
Now l certainly don't think it's that fast as the Ubuntu site says, and my current windows system is certainly on a par, if not better.
As this is the first time using dual boot and the new Ubuntu OS, can someone just explain the basic principle to me.
When l first start up and boot from the D drive to get Ubuntu working, is Windows on the C drive also working somehow?
Could this be why Ubuntu isn't that fast?
Just curious that's all.
Many thanks
WTC

---

### Post by sandyd on 2011-12-12
> **willythecat said:**
> AMD Athlon ll X2 250, Windows XP Home SP3 (32-bit), 4gb ram, partitioned C drive (C/D) and an F drive.
Hello everyone,
Have JUST downloaded Ubuntu 11.10 (64-bit) using "wubi"(?) onto my D drive and now have dual boot. 
Everything worked fine first time, but boy is it different! Having used XP for years, will certainly have to practice on this new OS! Looks good though.
Now l certainly don't think it's that fast as the Ubuntu site says, and my current windows system is certainly on a par, if not better.
As this is the first time using dual boot and the new Ubuntu OS, can someone just explain the basic principle to me.
When l first start up and boot from the D drive to get Ubuntu working, is Windows on the C drive also working somehow?
Could this be why Ubuntu isn't that fast?
Just curious that's all.
Many thanks
WTC
Running Ubuntu on Wubi is slower than running Ubuntu on a partition.
If you don't have anything in the "D" Drive, you can install Ubuntu onto it by burning Ubuntu onto a cd, and booting from the cd. Make sure you select the correct partition at install.

---

### Post by fantab on 2011-12-12
> **willythecat said:**
> AMD Athlon ll X2 250, Windows XP Home SP3 (32-bit), 4gb ram, partitioned C drive (C/D) and an F drive.
Hello everyone,
Have JUST downloaded **Ubuntu 11.10 (64-bit) using "wubi"**(?) onto my D drive and now have dual boot. 
Everything worked fine first time, but boy is it different! Having used XP for years, will certainly have to practice on this new OS! Looks good though.
Now l certainly don't think it's that fast as the Ubuntu site says, and my current windows system is certainly on a par, if not better.
**As this is the first time using dual boot and the new Ubuntu OS, can someone just explain the basic principle to me.**
When l first start up and boot from the D drive to get Ubuntu working, is Windows on the C drive also working somehow?
Could this be why Ubuntu isn't that fast?
Just curious that's all.
Many thanks
WTC

WUBI runs from within Windows. It adds an entry in the Winows MBR/boot menu for Linux. Ubuntu is installed within a file in the Windows file system and not on its own Partition. WUBI is not meant to be used as a permanent install method. It only facilitates Windows Users to try Ubuntu from windows and can be removed by Windows ADD/REMOVE Programs. 

This Method has its own limitations and issues. If you have finished TRYING, then it is strongly recommended that you MOVE to regular and full installation of Ubuntu. 

Ubuntu, on its own, in a dual-boot set up is completely different thing. The basic idea behind Dual-Boot is, IMO, to facilitate the migration from Windows to Linux. There may be applications and Games that you love and that these are Windows Specific. They are not available for Linux Platform. Also the scenario could be that at the workplace you only use Windows to earn your bread but personally you want to use Linux. Yes, there are Linux alternatives to most of the common Windows Applications, yet your comfort, familiarity and SKILL with the Windows Apps is something you don't want to lose. 

My advice, if you ask me, would be that you INSTALL UBUNTU TO ITS OWN PARTITION. The only effect this has on Windows (if you have only one hard disk) is that GRUB2 (Linux Boot Loader) from Ubuntu/Linux will replace Windows Boot Loader. GRUB2 is far better than Windows Boot Loader and will not affect Windows OS in any way.

For more information on Dual-Boot [**SEE THIS**]("http://members.iinet.net.au/%7Eherman546/index.html").
Also [**SEE THIS**]("http://linux.oneandoneis2.org/LNW.htm") to understand what is Linux as opposed to Windows or Mac.

Hope this helps.

---

### Post by Mark Phelps on 2011-12-13
First of all, despite what you've been told, you can NOT install Ubuntu to an NTFS partition in a normal install.  Only Wubi does that.

Also noticed you listed C, D, and F.  What is on "E"?  Your CD/DVD drive?

Asking because you can only have four primary partitions, and if "E" is already being used as a partition, you have reached your limit -- and would have to remove one to create an Extended partition for Ubuntu.

---

### Post by asifnaz on 2011-12-13
> **willythecat said:**
> AMD Athlon ll X2 250, Windows XP Home SP3 (32-bit), 4gb ram, partitioned C drive (C/D) and an F drive.
Hello everyone,
Have JUST downloaded Ubuntu 11.10 (64-bit) using "wubi"(?) onto my D drive and now have dual boot. 
Everything worked fine first time, but boy is it different! Having used XP for years, will certainly have to practice on this new OS! Looks good though.
Now l certainly don't think it's that fast as the Ubuntu site says, and my current windows system is certainly on a par, if not better.
As this is the first time using dual boot and the new Ubuntu OS, can someone just explain the basic principle to me.
When l first start up and boot from the D drive to get Ubuntu working, is Windows on the C drive also working somehow?
Could this be why Ubuntu isn't that fast?
Just curious that's all.
Many thanks
WTC
Wubi installer is there just to try Ubuntu . If you want to get real Ubuntu experience . Install it on a real partition

---

### Post by mastablasta on 2011-12-13
> **willythecat said:**
> AMD Athlon ll X2 250, Windows XP Home SP3 (32-bit), 4gb ram, partitioned C drive (C/D) and an F drive.
 
Curious, does 4GB work well out of the box with 32Bit WinXP HOME SP3. Want to upgrade my own maschine to 4 GB also using XP Home 32 bit.
 
> 
Now l certainly don't think it's that fast as the Ubuntu site says, and my current windows system is certainly on a par, if not better.

 
this can be due to:
1. running wubi which uses virtualisation of sort.  running propper dual boot might make it faster.
2. Ubuntu by default loads Unity interface which uses windows compositing /hardware acceleration to draw the desktop. so poor drivers support for your GPU in linux can be the source of problems. What graphics card do you have?
 
3. additionally using a 2D Unity interface should speed it up considerably. WinXP is 10 years old system. i don't think it even uses widnows compositing or any heavy effects to draw the deskotp environment. if it does it is limited. I think win 7 is the one that does. Ubuntu is new (2011).
 
To get a faster windows drawing and snappier OS try Xubuntu :-) with 4Gb it should fly.
 
I use Kubuntu (uses KDE - K desktop environment) and run it on 1.3 GB computer and old ATI 9600 graphics card. It runs much faster than windows. however opensource drivers for this card are very good. but they are not so good for some other older cards. I know that my bro with similar setup as yours and old ATI card had major graphics issues when he attempted live boot. point is perfomance of OS varies from system to system.

---

### Post by willythecat on 2011-12-13
[SIZE=2]Thanks everyone for the replies, most helpful, explains why it is a bit slower then.
 
MARK - excuse me why l search for some marbles underneath the desk, as l think l've just lost some of mine!
C/D, and F. What am l thinking? Meant to say C/D and E!
 
MASTA - Have an MSI 760GM E51 mobo. The 4gb ram is the maximum that can be used for 32bit, but this is immediately reduced to approx. 3.25gb once the system etc grabs what it needs. To install more than 4gb, and use it, then you need the 64bit OS (but you probably know this anyway). It also depends on the amount of "junk" installed, but my machine absolutely flies along.
 
Will therefore think about copying to CD, booting from this, and using the D partition for the install (without the dual boot).
Regards
WTC
[/SIZE]

---

### Post by mastablasta on 2011-12-13
> **willythecat said:**
>  
[SIZE=2]MASTA - Have an MSI 760GM E51 mobo. The 4gb ram is the maximum that can be used for 32bit, but this is immediately reduced to approx. 3.25gb once the system etc grabs what it needs. To install more than 4gb, and use it, then you need the 64bit OS (but you probably know this anyway). It also depends on the amount of "junk" installed, but my machine absolutely flies along.[/SIZE]

[SIZE=2]Thanks. i read you need to add PAE kernel to the XP home and even then Windows OS takes 1 GB the rest (3GB) you can use. i am just curious if it works out of box, need to add PAE kernel, is part simply not recognise etc. I think i might increase it to 4GB if i have the money. i have 2 now but some games are running slow and also the os needs some cleaning...[/SIZE]

> 
[SIZE=2]Will therefore think about copying to CD, booting from this, and using the D partition for the install (without the dual boot).[/SIZE]
[SIZE=2]Regards[/SIZE]
[SIZE=2]WTC[/SIZE]

 
[SIZE=2]to do that, simply delete D partition (asuming there is nothing else on it) in windows disk manager, then boot the CD and simply chose to install to largest unnocupied disk space (which would be the former D parition). the rest is done more or less automaticly. Should be over in about 15 minutes.[/SIZE]

[SIZE=2]Here is how it looks like for 11.10 (pics included): [/SIZE][[SIZE=2]http://www.psychocats.net/ubuntu/installing[/SIZE]]("http://www.psychocats.net/ubuntu/installing")
 
[SIZE=2]additionally disks in linux are marked with numbers. so parittion C would probably be sda1 (or hda1), then D would be sda2 (or hda2) etc.[/SIZE]

[SIZE=2]Anyway what i want to say is be on the lookout so you don't overwrite you system disk.[/SIZE]

---

### Post by robgraves on 2011-12-13
> **willythecat said:**
> [SIZE=2]Thanks everyone for the replies, most helpful, explains why it is a bit slower then.
 
MARK - excuse me why l search for some marbles underneath the desk, as l think l've just lost some of mine!
C/D, and F. What am l thinking? Meant to say C/D and E!
 
MASTA - Have an MSI 760GM E51 mobo. The 4gb ram is the maximum that can be used for 32bit, but this is immediately reduced to approx. 3.25gb once the system etc grabs what it needs. To install more than 4gb, and use it, then you need the 64bit OS (but you probably know this anyway). It also depends on the amount of "junk" installed, but my machine absolutely flies along.
 
Will therefore think about copying to CD, booting from this, and using the D partition for the install (without the dual boot).
Regards
WTC
[/SIZE]

Just so you know the drive designations C,D, E..etc are a windows thing, so it will not only lose being known as drive D, but if you do a proper ubuntu installation, you will probably format the drive as ext3 or ext4 which from within windows will be unrecognizable, to windows it will seem as if the drive doesn't even exist, but within ubuntu, you can see and even access the windows partitions, i personally have a multiboot system and i have a partition that is formatted FAT32 and known as "Cross OS Storage" that i put music, videos, pdf's, and other files in for easy access from windows and linux.

---

### Post by mastablasta on 2011-12-13
you can add a programme or addon and see also linux files from windows.

---

### Post by willythecat on 2011-12-13
[SIZE=2]Blimey, all sounds a bit complicated for the likes of me, as l'm not that brill about the ins and outs of things. 
Think l'll just stick with dual boot for now then, as l don't want to lose Windows, and just have a mess around with Ubuntu.
MASTA - Sorry if l'm waffling on, am not too technical, but seems you're situation is similar to mine, but with less ram.
First off, go to Crucial at  [http://www.crucial.com/](http://www.crucial.com/) and select their memory advisor/scanner. This will tell you what memory you have, what it can be upgraded to, and what type you need to buy.
I also had 2gb originally on an older mobo but had to junk this as l got a new mobo. Ordered my 4gb from crucial, out the box, plugged it in, and voila, an instant 4gb ram!
However, this will only give you 3.25gb free ram on a 32bit system.
You've lost me on the PAE kernel part, although l have googled it so l sort of know what you are talking about. Sorry, but don't know the answer to this.
Regards
WTC
[/SIZE]

---

### Post by mastablasta on 2011-12-14
It's not too complicated. You go into windows disk manager and delete the D partition (deleting will also remove any data on it). then you just install it next to existing operating system (as seen in the instructions link).
 
it is much safer than wubi once it is installed. 
 
Well i am not sure maybe it is only possible on win XP professional:
[http://msdn.microsoft.com/en-us/windows/hardware/gg487508](http://msdn.microsoft.com/en-us/windows/hardware/gg487508)
[http://msdn.microsoft.com/en-us/library/windows/desktop/bb613473(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/bb613473(v=vs.85).aspx)
[http://msdn.microsoft.com/en-us/library/aa366778.aspx#physical_memory_limits_windows_xp](http://msdn.microsoft.com/en-us/library/aa366778.aspx#physical_memory_limits_windows_xp) 
You are actually using only 3 GB ram. 1GB is probably being idle there. and in either case 32 bit applicaitons that run open it use up to 2 Gb ram anyway.... but it seems some other things might acces the higher ram.
 
i don't think i will upgrade just yet, cause i also have single core processor and i see that new dual/quad core ones won't fit into this socket. so i will likely save fore new motherboard (or new computer) as well :-)
 
PEA Kernel is the kernel (core of the operating system) that uses special addressing so it can use 4 or more GB ram on 32 bit operating systems. 32 bit Linux also has it, though you can also run 64Bit version.

---

