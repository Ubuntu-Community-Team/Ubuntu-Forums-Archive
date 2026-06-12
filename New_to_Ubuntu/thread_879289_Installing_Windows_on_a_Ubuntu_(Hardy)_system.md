---
title: "Installing Windows on a Ubuntu (Hardy) system"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by poligarcia on 2008-08-03
Hi!
About a year ago I turned completely from Windows to Ubuntu after dualbooting for some time. The thing is that although I0m completely happy with my Hardy now I need to dualboot again and I'm having some troubles to accomplish it. I'm following the instructions from [here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") but I'm not able to make the Windows XP installer to recognize the empty partition (I want XP, not Vista). I tried with a Windows XP SP1a, SP2 and SP3 CDs. The specific problem is that the Windows installer only sees a big partition (all of my disk) instead of the three partitions (Ubuntu, empty for Windows and swap).

Does someone know how to solve this?

Some more info, if I fdisk -l I get this:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            8052        9607    12498570    7  HPFS/NTFS
/dev/sda3   *           1        8051    64669626   83  Linux
/dev/sda4            9608        9729      979965    f  W95 Ext'd (LBA)
/dev/sda5            9608        9729      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by adult swim on 2008-08-03
i dont think windows will install on a non bootable partition.  so if youre going to use sda1 youll need to flag that as bootable

---

### Post by kansasnoob on 2008-08-03
Can you post a screenshot from Gparted (partition editor)?

I'd prefer a screenshot while mounted in Hardy so you may have to install Gparted:

```
sudo apt-get install gparted
```

Then go to System > Administration > Partition Editor and take a screenshot.

Example:

[ATTACH]80121[/ATTACH]

---

### Post by SunnyRabbiera on 2008-08-03
Just be careful and and back up your stuff, then set a decent sized partition for windows and make sure to be careful when installing XP as it will want to take up the entire drive.

---

### Post by poligarcia on 2008-08-03
Here it goes:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=80122&stc=1&d=1217816374[/IMG]

---

### Post by SunnyRabbiera on 2008-08-03
Looks fine to me, something like that will probably work but you may want to up the space windows takes a bit more.
With all the security patches, antivirus, anti spyware, anti addware and crap you will need it.

---

### Post by kansasnoob on 2008-08-03
OK, so sda1 is where you want Windows to go, eh? Is there any data on sda1? If you want to see you can install either ntfs-config or ntfsprogs to read the data on sda1.

Then click on sda1 and "delete"! That will give Windows a worry free space to install to. The installer will ask you whether to use NTFS or FAT32.

As it is the Win installer sees sda1 (the NTFS space) as used space. You want it to be "grey" space like that tiny bit of crap at the end of my screenshot.

BTW, I've had considerably more trouble installing SP3 than I did SP2.

Wait and I'll dig out a tutorial if you'd like.

Any questions?

Better safe than sorry.

---

### Post by poligarcia on 2008-08-03
> so if youre going to use sda1 youll need to flag that as bootable
I tried this but didn't work. :S

---

### Post by kansasnoob on 2008-08-03
> You want it to be "grey" space like that tiny bit of crap at the end of my screenshot.

Actually that APC guide shows that too:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

I've just kind of given up on them because they recently "hosed" the Vista guides. Sad because they had them just right!

But I think you're going to have boot problems and since your partitions are a bit "out of order" I'll post some mods to APC"s guide.

---

### Post by poligarcia on 2008-08-03
> then set a decent sized partition for windows
I think 9 Gb is enough for Windows, isn't it?

---

### Post by kansasnoob on 2008-08-03
> **poligarcia said:**
> I tried this but didn't work. :S

Have you tried with sda1 completely unformatted (greyed out)?

---

### Post by kansasnoob on 2008-08-03
> **kansasnoob said:**
> Have you tried with sda1 completely unformatted (greyed out)?

Or if sda1 has data that you want to keep we need to resize sda3.

There is something else we can try. You'd have to run the Ubuntu Live CD and then use Gparted to "move" sda3 to the right and leave the unformatted space at the left, but I don't think that's necessary.

---

### Post by poligarcia on 2008-08-03
> **kansasnoob said:**
> OK, so sda1 is where you want Windows to go, eh? Is there any data on sda1? If you want to see you can install either ntfs-config or ntfsprogs to read the data on sda1.

Then click on sda1 and "delete"! That will give Windows a worry free space to install to. The installer will ask you whether to use NTFS or FAT32.

As it is the Win installer sees sda1 (the NTFS space) as used space. You want it to be "grey" space like that tiny bit of crap at the end of my screenshot.

BTW, I've had considerably more trouble installing SP3 than I did SP2.

Wait and I'll dig out a tutorial if you'd like.

Any questions?

Better safe than sorry.
> OK, so sda1 is where you want Windows to go, eh?
Yeah !
> Is there any data on sda1?
No

> Then click on sda1 and "delete"! That will give Windows a worry free space to install to. The installer will ask you whether to use NTFS or FAT32.
As it is the Win installer sees sda1 (the NTFS space) as used space. You want it to be "grey" space like that tiny bit of crap at the end of my screenshot.
I already tried to install the WinXP with that partition unformatted with no results.

> Wait and I'll dig out a tutorial if you'd like.
If you find one that helps me I'll appreciate it :D

---

### Post by poligarcia on 2008-08-03
> **kansasnoob said:**
> Have you tried with sda1 completely unformatted (greyed out)?

Yes, but it didn't work. The Windows XP installer recognizes (as always) "Unpartitioned data" as big as my hard drive.

---

### Post by poligarcia on 2008-08-03
> **kansasnoob said:**
> Or if sda1 has data that you want to keep we need to resize sda3.

There is something else we can try. You'd have to run the Ubuntu Live CD and then use Gparted to "move" sda3 to the right and leave the unformatted space at the left, but I don't think that's necessary.

I heard that Windows requires to be installed on the beggining of the drive... is this true?

---

### Post by kansasnoob on 2008-08-03
> **poligarcia said:**
> I think 9 Gb is enough for Windows, isn't it?

Yes, for the basic system that's plenty, but drivers and such eat up a lot of space. ! have hardly anything on mine and it uses 12GB.

---

### Post by kansasnoob on 2008-08-03
> **poligarcia said:**
> I heard that Windows requires to be installed on the beggining of the drive... is this true?

No!

---

### Post by poligarcia on 2008-08-03
> **kansasnoob said:**
> Yes, for the basic system that's plenty, but drivers and such eat up a lot of space. ! have hardly anything on mine and it uses 12GB.

Ok, I'll take that into account.

---

### Post by kansasnoob on 2008-08-03
> Yes, but it didn't work. The Windows XP installer recognizes (as always) "Unpartitioned data" as big as my hard drive.

I've never had that happen. It always looks just like page four of the APC guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)

Like:

Partition Unknown ................
Unpartitioned space ...............
etc...................

So I'm puzzled! Are you certain that you've chosen to apply the changes in Gparted? When you close and then reopen Gparted does it show a greyed out area?

---

### Post by poligarcia on 2008-08-03
> **kansasnoob said:**
> Are you certain that you've chosen to apply the changes in Gparted? When you close and then reopen Gparted does it show a greyed out area?

Yes...
Maybe my case is special because I had first Windows XP, I reduced it with Partition Magic to install Ubuntu. After several months using it, I decided to remove Windows, so I deleted it with Gparted and Moved+Enlarged the linux partition.
Now I reduced it again, to make space for Windows, but cannot install it :(

---

### Post by kansasnoob on 2008-08-04
Well, it's odd to have sda3 as the first partition, but it's not unheard of.  In fact the windows installer generally only recognizes the "other" partitions as existing. It can't read ext 3.

But DUH! I'm not thinking!

You're trying to create a primary partition in  between a primary and an extended.

So you have a Ubuntu Live CD, eh?

If so boot the Live CD and use Gparted to delete that ntfs paertition, then "move" sda3 to the right! (Kind of makes a liar of me about win wanting to be #1 eh?) You could do the same by moving the extended partition to the left and then moving sda5 to the left.

These damn windows installers drive me nuts!!!!!!!!

Just make sure you have the Ubuntu partition and the swap partition (which is in an extended partition) located side by side, then try again.

---

### Post by kansasnoob on 2008-08-04
I'm about petered out, but if and when (I think it'll be when) you get Windows reinstalled you need to make some modifications to the APC guide's last page regarding restoring GRUB.

Where it says:

> To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd0,0)
- setup (hd0)
- quit
- exit 

That's all right except your GRUB will be on sda3 which means you need to change that list of commands to:

- root (hd0,2)
hit enter
- setup (hd0)
hit enter again
- quit
hit enter again
- exit
and enter again!

Then to add XP to the bootloader menu you need to know what the partition # is of your XP partition. I'm guessing it will be sda4, if so GRUB sees it as (hd0,3) because GRUB begins with 0 (yes, zero), so partition #1 is 0, #2 is (hd0,1), etc. The first number in (hd0,x) indicates the drive number, and since you have only one hard drive that number is always "0".

Clear as mud:confused:

So if XP is on sda4:

```
sudo gedit /boot/grub/menu.lst
```
title Windows XP
root (hd0,3)
makeactive
chainloader +1 

I hope you can get this done!

---

### Post by cjv8888 on 2008-08-04
Just a suggestion.
If you have an external harddisk, you can make an image of the sda3 on the external harddisk using a live CD, then you can install windoze and restore Ubuntu on a partition and restore grub, then you are back to the dual-booting.

---

### Post by poligarcia on 2008-08-06
Bad news, I moved the */dev/sda3* partition to the right (check the attachment), so Windows gets the inital part of the disk but again, the Windows XP installer recognized a big partition only. I must have something wrong with the partition table :(
I'm going to ask in a Windows forum or in th about this and let you all know if I get a solution.e [GParted forum]("http://gparted-forum.surf4.info/").
Of course, I could backup all and reinstall... but I prefer to find and fix the problem as it's funnier :)

---

### Post by poligarcia on 2008-08-06
Do you think these posts are related to my problem?

[LIST]
[*][Reinstalling XP on Dual-Boot System, partition problems]("http://ubuntuforums.org/showthread.php?t=577039")
[*][ Windows XP installer doesn't recognize partitions]("http://ubuntuforums.org/showthread.php?t=465570")
[*][I sadly need to repartition and install windows...but need a little help]("http://ubuntuforums.org/showthread.php?t=682757")
[/LIST]

---

### Post by kansasnoob on 2008-08-06
Just got home and saw your message, sadly I'm just clueless.

It looks like all three of the links to past posts also went unsolved.

The only thing I'd know to do at this point is to back up everything from your Linux partition and completely wipe the drive and start from scratch with Windows installed first.

Sorry I don't have a better answer.

---

### Post by poligarcia on 2008-08-06
What I think is wrong is the format of the Partition Table... I'm not an expert on the subject (not EVEN a newbie), but the problem makes me think there's something wrong eith the format in which Linux wrote the Patition Table, so that Windows XP installer cannot read it! What do you think about it?
Windows XP installer has some utils that I think can be used to fix the MBR (and partition table), *mbrfix* and *bootfix* which I'll check if those can help me.

---

### Post by poligarcia on 2008-08-06
Just to let you guys know, I posted a question on the [GParted Forum]("http://gparted-forum.surf4.info/viewtopic.php?pid=6768").

---

### Post by dlmoak on 2008-08-06
As an alternative, you might consider running Virtualbox on your system and installing Windows XP there.  I have two applications that I have to run at work that must be run under Windows.  I use virtualbox and everything works great.  I can even save the state of the virtual machine and get into the programs exactly where I was without having to boot Windows or load the two programs.  My machine at work has only an 80 gig hard drive and 1 gig of memory and all is working very well - no dual boot required.

---

### Post by poligarcia on 2008-08-06
> **dlmoak said:**
> As an alternative, you might consider running Virtualbox on your system and installing Windows XP there.  I have two applications that I have to run at work that must be run under Windows.  I use virtualbox and everything works great.  I can even save the state of the virtual machine and get into the programs exactly where I was without having to boot Windows or load the two programs.  My machine at work has only an 80 gig hard drive and 1 gig of memory and all is working very well - no dual boot required.

I already use VB on my system, but for this I need 3D acceleration, which is not working 100% yet on virtual systems (VirtualBox or VMWare).

---

