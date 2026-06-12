---
title: "Problem with partitions recogniton when trying to install Ubuntu."
date: 2016-03-15
forum: New to Ubuntu
---

### Post by petar6 on 2016-03-15
Hello guys, not sure if I have to post here or in the installation section.
 I'm new to Ubuntu(never used Linux before). When I try to install Ubuntu 14.04 it says no "operational system detected", when I try "something else", I don't see any of my partitions - it shows me my whole memory which is 1 TB.
I've read many guides, but I'm not sure how to proceed, as I'm new and "UEFI", "sudu/ " or something like this talks nothing to me :D . 

I'm using laptop Asus X552L, windows 10 pro(originally win 8.1, updated to 10).
When I installed my windows, I left some unallocated space for Linux later.
Here I attach some pics which I think can be useful:

[IMG]http://i.imgur.com/jW0cB9I.png[/IMG]

[IMG]http://i.imgur.com/l26o4tN.png[/IMG]

---

### Post by ajgreeny on 2016-03-15
See **Boot-Repair** in my signature and follow the instructions there to run the **Boot-info** script.
Post back here the pastebin link that script will give you and someone here will be able to assist you more.

---

### Post by Geoffrey_Arndt on 2016-03-15
Also . . . it's not unusual for the Ubuntu installer not to see Windows partitions (including unallocated) because Windows is hibernating - - so, it's not fully shut-down and the disk isn't available.    The Windows 8/10 option of "fast boot/fast start/quick start" (or similar as the terms seem to vary) *must be disabled.   *As I haven't used windows in 7 years or so, I can't say for certain how to do that in Win10 - - but look around in power settings or other setup options.   Note that if your Win10 is installed in UEFI mode, then Ubuntu must also be installed in UEFI mode (not legacy), and same for legacy (although there are downsides to running in Legacy mode).

---

### Post by petar6 on 2016-03-15
I got this from Boot Repair
[http://ubuntuforums.org/showthread.php?t=2317306](http://ubuntuforums.org/showthread.php?t=2317306)

Geoffrey, as the top picture says, my windows is installed in Legacy mode, but I'm not sure what that means and don't know how to install Ubuntu also in Legacy mode

---

### Post by ajgreeny on 2016-03-15
Sorry petar6 but your link is not for the report but back to this thread.

Can you give us the correct Boot-info report link, please.

---

### Post by petar6 on 2016-03-15
Sorry, wrong link :D
This is the right one

[http://paste.ubuntu.com/15393774/](http://paste.ubuntu.com/15393774/)

---

### Post by grahammechanical on 2016-03-15
Have have posted a link back to this thread & not to the Boot Repair pastebin URL.

There is no way to explain things without using unfamiliar terms. You have to accept that.

Motherboards have a built in boot system that defines the how the machine becomes a computer. It makes it possible to configure the working of the motherboard in different ways.

On older motherboards this boot system was called BIOS = Basic Input Output System. On newer motherboards the boot system is called UEFI = Unified Extensible Firmware Interface.

On motherboards with UEFI we can change the settings to install an OS in either EFI mode or BIOS/Legacy/CSM (Compatibility Support Module) mode.

If one OS is installed in EFI mode and every other OS to be installed must also be installed in EFI mode. If one OS in installed in BIOS mode then every other OS to be installed must be installed in BIOS mode.

If a machine has Windows 8.1 pre-installed then usually Windows 8.1 would be installed in EFI mode. Likewise with Windows 10 pre-installed. But you have it installed in BIOS/Legacy mode. And this is unusual.

And it causes me to wonder about the partitioning table of the hard disk.

Motherboards with a BIOS boot system will have hard disks with an MBR (Master Boot Record) partitioning scheme that only allows a maximum of 4 primary partitions. Now if those 4 allocated partition slots are used up then it become impossible to install an other OS without over-writing the existing partitions.

The way around this problem was to use one of the four primary partition allocation and create a special primary partition called an Extended partition. Then inside the Extended partition we can create any number of Logical partitions.

Machines that have a UEFI boot system usually have hard disks with GPT (GUID Partition Table) partitioning scheme. With GPT we can have any number of partitions without the need to create an Extended partition or logical partitions.

So, the question I am asking is this. Does your hard disk use MBR partitioning or GPT partitioning. If it uses MBR partitioning then you have already used up the allocated 4 primary partitions allowed. And it is not possible to use that unallocated space to create an Extended partition for the purpose of creating 2 logical partitions to be used by Ubuntu.

If the hard disk has GPT partitioning then they should be no problem in turning that unallocated space into 2 partitions for Ubuntu or even more partitions should you want to. So, we come back to the fact that the Ubuntu installer does recognise the existence of another OS on that hard disk.

Regards.

EDIT: It is GPT

> 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

And so I waste my time. But then there is this

> 
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?

And so Boot Repair is confused as well.

---

### Post by petar6 on 2016-03-15
Thanks for your comment, I learned a lot. My windows is legal(free license for students by Dreamspark). I have no idea what causes that.

So if I install windows in UEFI mode, would it change something? And how can I do that?
Or I'm ****ed up :D

---

### Post by oldfred on 2016-03-15
Your Windows is installed in BIOS boot mode on MBR(msdos) partitioned drive.
But you reinstalled Windows over a UEFI install that uses gpt partitioning. And Windows only boots from gpt with UEFI or only with BIOS from MBR.
And when you installed in BIOS mode Windows converted drive from gpt to MBR, but left backup gpt partition table. Or Windows does not correctly convert from gpt to MBR.

You can use fixparts to remove gpt data, or reinstall Windows in UEFI boot mode. How you boot install media UEFI or BIOS is then how it installs and all systems really need to be installed in same boot mode.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

But with MBR you have the age old 4 primary partition limit. Gpt does not have primary, extended nor logical partitions and has a soft limit (user can change) of 128 partitions.
Ubuntu can install in logical partitions, but you must use one of the 4 primary partitions as the extended partitions that is somewhat like a container for as many logical partitions as you want. Windows only boots from primary partition in BIOS mode.

All of these apply then:

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by petar6 on 2016-03-15
You mean my previous DOS was in UEFI mode and my current windows is in BIOS mode, which is the main problem?

Thanks you for the reply, I will try to do what you said, if I fail I will search how to reinstall windows in UEFI boot mode.
As soon as I try it I will mark this post as [solved] (hopefully) :D

P.S. What I've read about installing windows in UEFI mode, says to delete all partitions until I see only unallocated space, and then click next, and that's it. But when do I make more partitions where I can store my data?

---

### Post by oldfred on 2016-03-15
Windows expects or creates these partitions for UEFI.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

Best then to use Windows own tools to shrink NTFS partition to make space for more partitions. And reboot immediately so it can run chkdsk. Do not create partitions with Windows, but use gparted.

      
 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Then more info on dual boot install of Ubuntu:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html) 

Even more info in link in my signature below.

---

### Post by lewdposter on 2016-03-15
:popcorn:

---

### Post by cariboo on 2016-03-16
I think you are going to run into problems with a separate /usr  partition that is only 2Gb. On my fairly fresh Xenial install /usr is already 3.7Gb.

---

### Post by oldfred on 2016-03-16
Do not mix but an UEFI boot partition and /boot partition in Ubuntu.
And it looks like Windows is installed in BIOS boot mode so you do not want a UEFI boot partition.
And best especially if just starting out to use default / (root) & swap partition. 
Later or if you understand partitions well, add /home as a separate partition and/or data partition(s). Often a shared NTFS is good if dual booting and keep all system partitions somewhat smaller.
I suggest / of 20 to 25GB and swap of 2GB if you do not hibernate. And hibernation is not recommended if dual booting. Then as much space as you may want for /home or data partitions.

---

