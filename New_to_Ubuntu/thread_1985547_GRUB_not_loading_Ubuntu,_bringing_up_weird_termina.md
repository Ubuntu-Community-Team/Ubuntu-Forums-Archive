---
title: "GRUB not loading Ubuntu, bringing up weird terminal"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by meesterpickle on 2012-05-23
I dual boot Windows 7 and Ubuntu, though I use Ubuntu entirely for day-to-day computing. Today I had to switch back to Windows to find an old file, but when I tried to boot back into Ubuntu this odd thing appeared:

[LEFT][I]GNU GRUB version1.99-21ubuntu3
Minimal bash-like line editing is supported. For the first word, 
TAB lists possible command completions. Anywhere else TAB 
lists possible device or file completions.

grub>_[/I]


I haven't been able to do anything with it and Google doesn't help much, hence why I've come to you. I'm fairly new to Ubuntu, so I ask that you don't use any advanced terminology. I'll try to answer questions to the best of my ability.

Thank you!
[/LEFT]

---

### Post by oldfred on 2012-05-23
Welcome to the forums.

Do you have any DRM software in Windows that might write serial numbers or other data into the area just after the MBR where grub has some data also? Flexnet was one of the more popular DRM rights managers and new versions of grub2 finds it and writes around it.

You may just need to reinstall grub2's boot loader to the MBR, but may have same issue next time you boot into Windows as DRM keeps updating also.

Yanni, just posted, he has a bug that he is fixing right now. If you want us to review your configuration, just run the Bootinfo report and by the time we have reviewed it I think bug will be fixed. (You would then have to redownload).
The liveCD downloads work, but you may have to wait a few hours to be sure to have the fixed version of the one you can install into the Ubuntu liveCD:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

Or you can manually reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by meesterpickle on 2012-05-23
So to summarize, I should download Ubuntu onto a cd or USB drive. Boot Ubuntu from there and then run BootRepair through it? I'm probably looking like an idiot, sorry.

---

### Post by YannBuntu on 2012-05-23
> **meesterpickle said:**
> So to summarize, I should download Ubuntu onto a cd or USB drive. Boot Ubuntu from there and then run BootRepair through it? I'm probably looking like an idiot, sorry.

Yes, this is a possibility.

- 2nd possibility (that i prefer): download an Ubuntu CD with Boot-Repair pre-installed ([https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)), boot on it, choose "Try Ubuntu", click on the Dash (the top-left Ubuntu logo), search and run Boot-Repair

- 3rd possibility : download [Boot-Repair-Disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/"), boot on it, it will automatically run Boot-Repair utility at startup.

---

### Post by meesterpickle on 2012-05-24
So I tried burning the UbuntuSecureRemix iso file on a CD-R and booting from it. It would just say "booting from disk" for a few seconds, then it would return back to the Windows Bootloader. I also tried the Boot-Repair-Disk and it did the same thing.

Any advice?

---

### Post by drs305 on 2012-05-24
Is your BIOS set up to boot the CD first? If not, change the setting.

If it is, try inserting a commercial, bootable CD of some sort and see if it works, just to verify the CD-ROM is operating correctly.

---

### Post by meesterpickle on 2012-05-24
Okay, so I set up my BIOS so that it checks for stuff in the CD drive before anything else. So it now it says "Booting from disk" before opening the bootloader, but still doesn't work. I wasn't able to try booting any "commercial" disks because I don't have any, but I did open some normal CDs and they worked fine.

I'm going to try booting that Ubuntu liveCD thing. Any advice or questions?

---

### Post by oldfred on 2012-05-24
Are  you installing the software to the CD correctly? You do not just copy an ISO to the CD.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by meesterpickle on 2012-05-25
I dragged the iso file to the blank cd, then it said that the file was waiting to be burned, so I clicked the "Burn Disk" button and it burned the file to the disk.

So I tried booting the liveCD thing, it did the same thing as the others. I also tried booting it on another computer in my house and it didn't work either, so maybe there is something wrong with the burning? (we all have the same model though, Dell Dimension E521).

---

### Post by mlentink on 2012-05-25
Wht are you using to burn it?
You might want to look here: [http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

or here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by mlentink on 2012-05-25
Meesterpickle simply dragging the iso-file to the cd and burning that ***file ***on the disc is not going to help. It's not the file, but the contents we want on that cd. Please review the links in earlier posts.

Since you're running windows 7, please read this first: [http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

### Post by meesterpickle on 2012-05-25
Huh, I wasn't doing it that way. I was dragging the file onto the disk, then clicking the "Burn to Disk" option. "Windows Disk Image Burner" seems to be specialized for iso files, so I'll try it with that. However, I'm out of disks so I'll need to go get more today.

Do you think it would make a difference?


EDIT:
Sorry, I was ninja'd by the previous poster. I'll make sure to use the correct method now, sorry.

---

### Post by meesterpickle on 2012-05-25
So, I got some more CD-Rs and burned that UbuntuSecureRemix thing on one using the correct method. I got some interesting results that you can see in the attachments. I can't even begin to understand what the heck happened... any ideas? Anyone?

---

### Post by oldfred on 2012-05-26
Are you able to run the Boot-Info from the other options tab?

Or directly download just the bootinfoscript as posted above and run it. 

It sounds like you are missing major parts of your system. But one of the reports would greatly help us in diagnosing your issues.

---

### Post by meesterpickle on 2012-05-26
Wait, is this boot-info thing in Ubuntu? I'm having trouble getting it to load Ubuntu at all now.

---

### Post by oldfred on 2012-05-26
It is part of Boot-Repair or a script you can download into most Linux installs, liveCDs or USBs. So if you can boot Boot-Repair you can run the Boot-Info report.

Or you can download the bash script and run the script from the Ubuntu liveCD.

---

### Post by meesterpickle on 2012-05-26
Okay, so I burned Boot-Repair to a disk like you said so that I could get the boot info. The boot-repair itself didn't fix anything, but I think I got the boot info thing you wanted: [http://paste.ubuntu.com/1008384/](http://paste.ubuntu.com/1008384/)

Hope that helps!

---

### Post by oldfred on 2012-05-26
It would have been nice to have told us you have wubi not a partition install. Wubi is a file inside Windows and it uses the Windows boot to boot. The grub menu is just to make it like a normal install but is not for multiple booting.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

With wubi, all I think Boot_repair can do is fix the Windows booting.

So what now is the original issue, I have forgotten. We need to start over. When you say weird terminal is it grub> , grub rescue> or a login and Ubuntu terminal?

There are some others here that know wubi better.

---

### Post by meesterpickle on 2012-05-26
Sorry about giving incorrect information... I guess I was confused.

When I try to start Ubuntu, this is the terminal I see:

[I]GNU GRUB version1.99-21ubuntu3
 Minimal bash-like line editing is supported. For the first word, 
 TAB lists possible command completions. Anywhere else TAB 
 lists possible device or file completions.

 grub>_[/I]



So grub> I suppose.

---

### Post by oldfred on 2012-05-26
Lets see if this works:

Type this at "grub sh>" prompt:

```
set path=/ubuntu/disks/root.disk
linux /vmlinuz root=/dev/sda2 loop=$path ro
initrd /initrd.img
boot

```

---

### Post by YannBuntu on 2012-05-26
Hello

> **oldfred said:**
> With wubi, all I think Boot_repair can do is fix the Windows booting.

FYI, B-R also:
- mounts (loop) the Wubi partition and opens it in a file browser, in order to let the user easily access and backup the Wubi /home if necessary.
- proposes a [filesystem repair of the root.disk]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") (and home.disk if it exists)

I'm not a Wubi expert either, so don't hesitate to suggest other features.

---

### Post by meesterpickle on 2012-05-26
I'm at the grub> prompt, not the "grub sh>" prompt.

When I typed in *linux /vmlinuz root=/dev/sda2 loop=$path ro* I got an error saying the file wasn't found.

---

### Post by oldfred on 2012-05-26
This may fix corruption, if that is why it cannot read it correctly.

```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

```
Note space in mount command between /dev/sda2 and /media/win

---

### Post by meesterpickle on 2012-05-26
It says that grub doesn't understand commands like "sudo". Are we talking about the same grub here?

---

### Post by oldfred on 2012-05-26
Sorry, you need to run those command from a terminal in a liveCD.

---

### Post by meesterpickle on 2012-05-26
So I tried the Ubuntu liveCD again and it worked! I'm not certain about the code though. I put a screen capture in the attachments.

---

### Post by oldfred on 2012-05-26
I guess I should have noticed earlier. The script finds wubi files but not the main wubi file root.disk

> /mnt/BootInfo/sda2/ubuntu/disks/root.disk: Input/output errorDid root.disk get deleted? Or did you run chkdsk and it removed it or renamed it?
Windows chkdsk can put files it has issues with in a chkdsk folder.

All your Ubuntu files were in the root.disk inside the NTFS partition.
It relies on Windows. One of the reasons we often suggest a full partitioned install if you like Ubuntu.

---

### Post by bcbc on 2012-05-27
This is what I recommend whenever a wubi install boots to a grub prompt: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by meesterpickle on 2012-05-27
I read the guide. I still have my root.disk though and I couldn't find the *C:\found.0000* folder, even when I had it show protected OS files. The command prompt code returned "The system cannot find the path specified".

I think I'm going to cut my losses and reinstall Ubuntu with a proper partitioned installation. Could I do that without needing to uninstall wubi?

---

### Post by oldfred on 2012-05-27
If you have room you can shrink Windows and create new partitions. Best to use Windows 7 to shrink Windows, but it really likes at least 30% free space to work well. But do not create partitions with Windows as it cannot create Linux partitions and may convert to dynamic which does not work with Linux.

Best to do a full backup of Windows:
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by bcbc on 2012-05-27
> **meesterpickle said:**
> I read the guide. I still have my root.disk though and I couldn't find the *C:\found.0000* folder, even when I had it show protected OS files. The command prompt code returned "The system cannot find the path specified".

I think I'm going to cut my losses and reinstall Ubuntu with a proper partitioned installation. Could I do that without needing to uninstall wubi?
Did you run chkdsk? You need to run it. 

You might need to even if you want to uninstall as it could prevent deletion of the Ubuntu directory

---

