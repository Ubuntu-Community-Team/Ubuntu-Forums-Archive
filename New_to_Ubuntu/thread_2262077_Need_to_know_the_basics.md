---
title: "Need to know the basics"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by mandarpowale on 2015-01-22
I want to know the basics of installing UBUNTU LINUX on my system. I want to know how partitions are made and labelled. What are its limitations. I am a windows user and I am not 
so familar with UBUNTU LINUX. 

I want to browse the net and be able to play games on UBUNTU, (STEAM GAMES)


ADD

My personal computer configuration is

AMD XII 260 3.2GHz
ASUS M4N68T-M LE V2
4GB DDR III 1333MHz Gskill RAM
ASUS HD7750HD-1GD5-V2
1 TB WD Purple HDD (C:\ 250 GB, E:\250GB & F:\431 GB)
500GB WD Green HDD(D:\150 GB(bad sector), G:\150GB, H:\172GB)
CIRCLE 500W Raw Power PSU.

I have Win 7 X64 SP1, Ult on C:\

I wanted to install Linux on E: and be able to run DOTA 2, Counter-Strike 1.6 & Left 4 Dead 2. I tried to find Linux drivers for my graphic card on ASUS website, but they don't have them.

Regards,
Mandar Powale

---

### Post by QIII on 2015-01-22
Hello!

That's a pretty broad question.  I suggest you start with [this]("http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install") and then have a look at [this]("https://help.ubuntu.com/community/Installation") for more detail.  If  you plan to dual boot with Windows, there are some detailed considerations, which we'll help with.  It that is what you are going to do, it is important that you select "Something else" when it comes to partitioning so you don't lose your Windows installation.

If most of it goes over your head, we'll be happy to answer specific questions.  Ask before you do anything.

Cheers!

---

### Post by mandarpowale on 2015-01-25
Thanks QIII , I will read the guide and then post questions if any arise.

---

### Post by greg69 on 2015-01-25
There's not a great deal of stuff to know about partitioning unless you're dual booting. We need to know if you're planning a dual boot, And if you are, There's an install function which allows for installation alongside an OS. I'd advise installing Windows FIRST to avoid it panicking and wiping the drive.

All essential packages are already installed and other ones you need are available via Ubuntu software centre. Such as Steam.
If you don't use steam, There's a few good games on the software centre like OpenArena and Nexuiz. You can also pick up some non steam games like Kerbal Space Program.

---

### Post by mandarpowale on 2015-01-26
> **greg69 said:**
> There's not a great deal of stuff to know about partitioning unless you're dual booting. We need to know if you're planning a dual boot, And if you are, There's an install function which allows for installation alongside an OS. I'd advise installing Windows FIRST to avoid it panicking and wiping the drive.

All essential packages are already installed and other ones you need are available via Ubuntu software centre. Such as Steam.
If you don't use steam, There's a few good games on the software centre like OpenArena and Nexuiz. You can also pick up some non steam games like Kerbal Space Program.

I want to dual boot with windows, initially and I just want to use one of my 250 GB partitions for UBUNTU. Does UBUNTU format in NTFS?

---

### Post by Dennis N on 2015-01-26
> Does UBUNTU format in NTFS? 
1) Ubuntu itself must be installed on a partition with the ext4 filesystem. 
2) Ubuntu has tools to format a filesystem as NTFS.

---

### Post by mandarpowale on 2015-01-26
Thanks Dennis

Can I use the entire 250 GB partition for UBUNTU?

Regards, 
Mandar

[COLOR=#000000]I want to know the basics of installing UBUNTU LINUX on my system. I want to know how partitions are made and labelled. What are its limitations. I am a windows user and I am not [/COLOR]
[COLOR=#000000]so familar with UBUNTU LINUX. [/COLOR]

[COLOR=#000000]I want to browse the net and be able to play games on UBUNTU, (STEAM GAMES)[/COLOR]


[COLOR=#000000]ADD[/COLOR]

[COLOR=#000000]My personal computer configuration is[/COLOR]

[COLOR=#000000]AMD XII 260 3.2GHz[/COLOR]
[COLOR=#000000]ASUS M4N68T-M LE V2[/COLOR]
[COLOR=#000000]4GB DDR III 1333MHz Gskill RAM[/COLOR]
[COLOR=#000000]ASUS HD7750HD-1GD5-V2[/COLOR]
[COLOR=#000000]1 TB WD Purple HDD (C:\ 250 GB, E:\250GB & F:\431 GB)[/COLOR]
[COLOR=#000000]500GB WD Green HDD(D:\150 GB(bad sector), G:\150GB, H:\172GB)[/COLOR]
[COLOR=#000000]CIRCLE 500W Raw Power PSU.[/COLOR]

[COLOR=#000000]I have Win 7 X64 SP1, Ult on C:\[/COLOR]

[COLOR=#000000]I wanted to install Linux on E: and be able to run DOTA 2, Counter-Strike 1.6 & Left 4 Dead 2. I tried to find Linux drivers for my graphic card on ASUS website, but they don't have them.[/COLOR]

[COLOR=#000000]Regards,[/COLOR]
[COLOR=#000000]Mandar Powale[/COLOR]

---

### Post by mansonfan78 on 2015-02-03
> **mandarpowale said:**
> Thanks Dennis

Can I use the entire 250 GB partition for UBUNTU?

Regards, 
Mandar

Yes you can, but I would suggest splitting into multiple partitions:  ~25gb formatted as ext4, mounted as /, a small partition equal to or slightly larger than your ram as swap space, and the remainder as ext4 mounted as /home (at least 20gb to be safe).  You could also create a separate ntfs partition for your files that could be shared by both operating systems (linux can read/write ntfs without problems).

---

### Post by mastablasta on 2015-02-03
> **mandarpowale said:**
> 
Can I use the entire 250 GB partition for UBUNTU?


why not? you need to delete the partition first so it becomes emtpy disc space then all you have to do is to select in installer to install into largest free disk space. all toher necessary parittions will be created automatically.

forget about NTFS. Linux can use it as data partition but not as OS partition. permissions are set completely different in Linux than in windows. and NTFS can not handle it. it is a very old file and not very advanced files system. by default Ubuntu uses Ext4. however you can choose a few others. looks like BTRFS will be the next file system. it features snapshots among other things. but for now it is sort of still beta.

one more thing - everything is a file in Linux. 

> **mandarpowale said:**
> [COLOR=#000000]. I tried to find Linux drivers for my graphic card on ASUS website, but they don't have them.[/COLOR]


for drivers you have additional drivers utility. you launch that it will detect the GPU and offer you to install closed source drivers (by default you have open source ones). you select the one you would like to use and click install. yes it's that simple. they will also get automatic updates along with the rest of the apps in the system.

also I will assume this here is the GPU HD7750HD - so AMD drivers - the closed source ones are now only slightly better then opensource ones as AMD is working to open them completely it seems. in any case for gaming oyu would need the closed source ones, but otherwise the default opensource should be fine.

---

### Post by JeQhdMD on 2015-02-03
What type of disk operating system at the firmware level?   Is your system based on UEFI/GPT partioning or a standard BIOS?   Very important to check and know before formulating an install plan.

---

### Post by kingdominsight on 2015-02-04
I have a similar system
First of all you can run Ubuntu from the CD to see if you like it first. If you decide to install it I would advise doing a low level format on the HD before installing a New OS.
For example i installed Ubuntu over Mint and found items in the waste  basket from the previous Linux install, I can't explain this, it just  happened.

Here is the site for the HD7750 drivers.
[http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)
Your graphics card Just does fall into ATI's support for the new Linux kernel.
However Installation can be kind of tricky. I would advise getting to know your new OS and use the provided open source drivers for a while untill you get to know how to use the terminal a little bit.

---

### Post by mandarpowale on 2015-02-04
Thanks QIII and mastablasta

Thanks to everyone who has helped me so far

I have installed UBUNTU to dual boot with windows as instructed by [mansonfan78]("http://ubuntuforums.org/member.php?u=1424979")

my partitions are '/' 25 GB SWAP 16GB and '\home'  (250GB minus 25GB Minus 16GB)

> "one more thing - everything is a file in Linux."

Can you please elaborate on that?

> for drivers you have additional drivers utility. you launch that it will  detect the GPU and offer you to install closed source drivers (by  default you have open source ones). you select the one you would like to  use and click install. yes it's that simple. they will also get  automatic updates along with the rest of the apps in the system.


please name the utility and how to do so.

I would also like to know what the other options during installation were (Options other than '/', "swap" and '/home'

I currently plan to install steam and then use its backup and restore utility to install my steam games, I will also download UBUNTU update during night. I also need to know where my steam games will go (in the 25GB '\' partition or '\home' partition ?

Please reply ASAP.

---

### Post by Bucky Ball on 2015-02-04
You don't need anything like 16Gb for /swap unless you intend to hibernate. Then it should be the same size or slightly larger than your installed RAM. Ubuntu boots pretty quick (or should) so hibernation is a little redundant. 2Gb /swap is fine.

You can open Gparted, switch /swap off (right click it), shrink it to 2Gb, then switch it back on;

Unmount the partition next to it (presumably /data if you have /swap at the end of the disk, which is normal), right-click it and unmount, then expand it into the 14Gb unallocated space that is left by shrinking /swap.

You may need to inspect your current setup to figure what is the best way to resize your partitions. (PS: If you need to, you can't resize your / partition without unmounting it and you can't do that running from it, so you need to resize / running a Live session from USB or disk.)

Good luck.

---

### Post by mandarpowale on 2015-02-04
> **Bucky Ball said:**
> You don't need anything like 16Gb for /swap unless you intend to hibernate. Then it should be the same size or slightly larger than your installed RAM. Ubuntu boots pretty quick (or should) so hibernation is a little redundant. 2Gb /swap is fine.

You can open Gparted, switch /swap off (right click it), shrink it to 2Gb, then switch it back on;

Unmount the partition next to it (presumably /data if you have /swap at the end of the disk, which is normal), right-click it and unmount, then expand it into the 14Gb unallocated space that is left by shrinking /swap.

You may need to inspect your current setup to figure what is the best way to resize your partitions. (PS: If you need to, you can't resize your / partition without unmounting it and you can't do that running from it, so you need to resize / running a Live session from USB or disk.)

Good luck.

I want to know what 'bin', 'boot', 'cdrom' 'dev' 'etc , 'home'  'lib' 'lib64', 'media', 'mnt' opt proc root run sbin srv sys temp usr var inittrd.img vmlinuz stand for.

My RAM is 4GB, my hdd is 1TB WD Purple (250 Windows,250,460GB Data Partitions) and older 500GB (150 bad sector, 150 good and 172GB partitions). I had to buy 1TB since 500 GB WD Green hdd got bad sectors.

]I just want to know where my data will go if I install steam and games. I used my 250 GB partition to install Linux as suggested by mansonfan78 so the partitions stand as '/' 25 GB , 16 GB(since i wanna run games) and whatever remains as the part of 250 GB partition as '/home'. I want steam and games to be installed  in '\home'.

Also I don't want to change my partitions sizes unless '\' needs to be bigger. Also I don't know where to find and how to use GParted.

---

### Post by SeijiSensei on 2015-02-04
Most all programs reside in /usr/bin. Well-behaved programs should store users' data in their home directory.  Often these settings are located in "hidden" files, ones that begin with a dot.  Take a look at /home/username/.config for examples.

Do not try and relocate programs to other locations as you will break the updating process.  You don't need to fiddle with things like file locations, and doing so can break things.

Read this for details about how the Linux file system is organized.  It's very different from Windows:  [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by JeQhdMD on 2015-02-04
Also, Youtube videos are actually a better source of information about the type of questions you have.   Right now, after reading this thread, I would caution against learning about Linux in a quick and superficial manner... _YOU also have to take the initiative_ to investigate and help find some of these answers.  

For example, your saying "I don't know where to find and how to use Gparted" . . . did you actually try to google it, and use the ubuntu search tool in dash?  (ps, it is already installed).   Youtube has MANY videos on how to use it.

As good as these forums are, for me, I've found they don't begin to compare with learning about Linux in a basic college class (even online classes via Kahn Academy or similar) . . . or great books like the Ubuntu Handbook available on Amazon.

---

### Post by mandarpowale on 2015-02-04
> **JeQhdMD said:**
> Also, Youtube videos are actually a better source of information about the type of questions you have.   Right now, after reading this thread, I would caution against learning about Linux in a quick and superficial manner... _YOU also have to take the initiative_ to investigate and help find some of these answers.  

For example, your saying "I don't know where to find and how to use Gparted" . . . did you actually try to google it, and use the ubuntu search tool in dash?  (ps, it is already installed).   Youtube has MANY videos on how to use it.

As good as these forums are, for me, I've found they don't begin to compare with learning about Linux in a basic college class (even online classes via Kahn Academy or similar) . . . or great books like the Ubuntu Handbook available on Amazon.


No offence but I live in Mumbai , India and here they teach Red Hat in classes since it is the one that gets deployed in professional environment. However I'll try youtube and google search for learning advanced features.

Thanks for the advice.

If possible i'll try Kahn's Classes and the handbook too,

> **kingdominsight said:**
> I have a similar system
First of all you can run Ubuntu from the CD to see if you like it first. If you decide to install it I would advise doing a low level format on the HD before installing a New OS.
For example i installed Ubuntu over Mint and found items in the waste  basket from the previous Linux install, I can't explain this, it just  happened.

Here is the site for the HD7750 drivers.
[http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)
Your graphics card Just does fall into ATI's support for the new Linux kernel.
However Installation can be kind of tricky. I would advise getting to know your new OS and use the provided open source drivers for a while untill you get to know how to use the terminal a little bit.

Thanks.

---

### Post by JeQhdMD on 2015-02-04
1.  If you study Redhat - - it is also Linux and you will know how to learn the minor differences between it and Ubuntu (85% at least is the same operation and tools).
2.  You don't have to go to Bangalore to study Ubuntu - you probably have more opportunities there than in the US.
3.  Here is a local (mumbai) computer club very familiar with Ubuntu:   [https://lists.ubuntu.com/archives/ubuntu-in/2014-November/011576.html](https://lists.ubuntu.com/archives/ubuntu-in/2014-November/011576.html)

PS:  I retired as an IT professional and up to 40% of my fellow IT managers, consultants, engineers were from various places in India . . . we continue to hire people from India and our company uses Redhat as well as Suse and Ubuntu (Canonical is a leader on the cloud).   Those are the 3 big Linux companies (and you could to some extent add Debian also as well as traditional unix)

---

### Post by mansonfan78 on 2015-02-04
While 16 gb for swap (which is virtual memory) is excessive, it won't hurt anything unless you really need the extra drive space for something else.  I recommended having /home on a separate partition because should you ever need to reinstall the os you could then mount (but not format) /home during the reinstall and not lose any of your data.  It also comes in handy if you make regular backups of your hard drive - if something in one partition breaks or becomes corrupted you could restore that one partition without affecting anything else.

---

### Post by mandarpowale on 2015-02-04
I have backed up my steam games on a NTFS partition can I restore them ?

---

### Post by mansonfan78 on 2015-02-04
Yes, you could just copy them within your file manager to wherever they're supposed to be.

---

### Post by mandarpowale on 2015-02-05
I meant by 'backup and restore' utility in STEAM. I have posted the same question on steam boards too. Let us C.

> **JeQhdMD said:**
> What type of disk operating system at the firmware level?   Is your system based on UEFI/GPT partioning or a standard BIOS?   Very important to check and know before formulating an install plan.

Standard BIOS I think

It is a ASUS M4N68T-M LE-V2

I managed to get UBUNTU UP and Running and also managed to Install CS 1.6 on Steam now gonna try DOTA2 and Left 4 Dead 2. Will also try some of the games mentioned here.

Thanks for all the help.

> **kingdominsight said:**
> I have a similar system
First of all you can run Ubuntu from the CD to see if you like it first. If you decide to install it **I would advise doing a low level format on the HD before installing a New OS.**
For example i installed Ubuntu over Mint and found items in the waste  basket from the previous Linux install, I can't explain this, it just  happened.

Here is the site for the HD7750 drivers.
[http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)
Your graphics card Just does fall into ATI's support for the new Linux kernel.
However Installation can be kind of tricky. I would advise getting to know your new OS and use the provided open source drivers for a while untill you get to know how to use the terminal a little bit.

How do I do a low level format ? My motherboard doesn't have that feature.

---

### Post by JeQhdMD on 2015-02-06
Well., a complete formatting (aka low level format) removes _all content and OS's (windows, linux, partitions, boot loaders, etc_.).

I only do that when a machine is being removed from service and/or being sold.

---

### Post by mansonfan78 on 2015-02-06
> **kingdominsight said:**
> I have a similar system
First of all you can run Ubuntu from the CD to see if you like it first. If you decide to install it I would advise doing a low level format on the HD before installing a New OS.
For example i installed Ubuntu over Mint and found items in the waste  basket from the previous Linux install, I can't explain this, it just  happened.

Here is the site for the HD7750 drivers.
[http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)
Your graphics card Just does fall into ATI's support for the new Linux kernel.
However Installation can be kind of tricky. I would advise getting to know your new OS and use the provided open source drivers for a while untill you get to know how to use the terminal a little bit.

Just so you know: when Ubuntu (and Mint) install over the top of an existing linux os (even if "format" is selected) certain files and folders are not deleted.  Mostly it's /usr/share and it's subdirectories since that is where wallpapers and custom items are stored.  This is so that you can do a "clean install" without actually losing everything.  This could also include trash directories.

---

