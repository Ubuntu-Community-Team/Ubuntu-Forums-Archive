---
title: "dual boot with windows 7 problem.  windows doesn't boot"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by eggwardo on 2012-03-06
I have a netbook with windows 7 preinstalled on it.  I partitioned the hard drive and installed ubuntu 11.10 into the partitions.  Ubuntu is working fine but windows doesn't boot.  I see it in the grub menu but it just goes to a black screen with a blinking cursor when i select it.  I don't have a windows recovery disk, just a recovery partition on the hard drive, which i can get to but i don't want to run that because it looks like it will wipe out my computer.

I've been searching on this forum and found other people with the same problem but I'm not sure if any of the fixes worked (i didn't find a solved post).   One thing i did find is that you guys always ask for a boot repair report.  So here's that:     
[http://paste.ubuntu.com/872252/](http://paste.ubuntu.com/872252/)

The reason i'm installing ubuntu is to start to learn linux.  So obviously I am very much a noob at ubuntu and linux all together.  So please, any suggestions you have for me, please spell them out in very simple terms.  

thanks in advance to my new best friends,

---

### Post by oldfred on 2012-03-06
All NTFS partitions have to have a NTFS signature in the partition boot sector or PBR. You installed grub2's boot loader to the Windows boot sector.

    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 468071240 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

NTFS keeps a backup of the PBR, so if you only installed once you can restore the backup. Specific instructions on using testdisk to do that are here:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

#Another set of instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by eggwardo on 2012-03-07
Well i did that, I followed the 3rd links instructions because they seemed more complete. (this one [http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510) ).  But it still doesn't work.  
It appears that I (or testdisk or boot-repair) put the xp boot stuff in instead of windows 7.  (but I really don't know how)

My new boot repair log:
[http://paste.ubuntu.com/873841/](http://paste.ubuntu.com/873841/)

When i pick windows 7 from the grub screen it now shows a few characters in the top left and the blinking cursor.  It just stays on that black screen now,  where before it was only on it for a second or two and then went back to grub.

Any more advise would be greatly appreciated.  

Thanks

---

### Post by oldfred on 2012-03-08
There are some internal differences in the NTFS boot sectors for XP & Vista/7. One of the main one's is XP boot sector tells it to boot ntldr and 7 tells it to boot with bootmgr.

I ran chkdsk on my XP partition from a Windows 7 repairUSB and it put a 7 boot sector. I could see with testdisk it called out bootmgr but still booted my XP?? I put a XP boot sector back in with the Windows 7 repairUSB.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

Grub also remembers where to reinstall, so you may want to check that also.
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by eggwardo on 2012-03-09
Since I have a netbook i don't have a restore disk and I don't have a big enough usb stick to make a restore "disk" that way.
So I decided I would just restore my computer with the restore partition.   After rebacking up all of my files i went into the restore thing and noticed an option (that i didn't see before) that would keep all of my files in tact.  I ran that, and 4 hours later nothing changed.  Still the same issue when i try to start windows, and Ubuntu still works.

I guess tonight i'll just do the wipe computer restore option.  

It's very possible that i misunderstood what you thought i should do.  If you want to explain anything else i'm all ears.

thanks again

---

### Post by oldfred on 2012-03-09
I created the Windows 7 repairCD and USB. I was trying to directly convert the repair ISO to a USB using Ubuntu but could not. But it did work to create the CD and use the CD to create the repairUSB. The repairUSB was only about 30K.

If you know someone with a Windows 7 computer that is the same 32bit or 64bit.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by eggwardo on 2012-03-09
Well i'm glad you tried to convert the ISO directly to the USB.  I was going to try that and I'm sure it would have taken me way longer to realize it wasn't possible than you.
I've been asking and I don't know anyone with a windows 7 computer.   

I do have a vista computer.  Are you saying i could use that to make the repair usb?

thanks again

---

### Post by oldfred on 2012-03-09
I think the instructions say you can, if you have the service packs installed, but you have to boot into Vista to make the repairCD/USB.

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Another download site Despotism Believed to be ok.
[http://ubuntuforums.org/showpost.php?p=11249721&postcount=439](http://ubuntuforums.org/showpost.php?p=11249721&postcount=439)

---

### Post by eggwardo on 2012-03-16
Well, It took a while but i got someone to make me a repair disk.  (those links you posted didn't work anymore)  But then the disk they made was 64 bit so i didn't want to try it.  So i just got a torrent of the 32 bit version, made the repair USB, ran it, and it didn't work.
So i downloaded a torrent of windows, but i made sure to get one that wasn't cracked.  So i didn't break the law, I think
Before i installed i tried to repair from the install disk and that still didn't work.  So i reinstalled windows.  Obviously that worked.  Thanks for helping me with this.

But i do have one final question.

When i try my dual boot again,  which partition do i put grub in?
I put it in SDA2 before which is windows boot partition.
I'm guessing it was supposed to go it SDA3 which was the main windows partition.
Please let me know so i don't have to re-reinstall.

thanks again

---

### Post by oldfred on 2012-03-16
Boot loaders go into the MBR or just sda, not sda1 or sda2 etc which are the partitions in Linux. 

Grub will let you boot both Ubuntu and Windows, where Windows does not boot Linux.

---

### Post by eggwardo on 2012-03-16
Thanks OldFred!!

I ended up with a reinstall but your help was greatly appreciated.  Now i know what i did wrong.  I was iffy on where to put grub the first time and obviously it would have paid off to be patient and do some research. Or wait until i'm sober.  

I do now have a properly running dual boot computer.

Do you have a donate button anywhere (i'm pretty sure i saw you somewhere else recently, probably something to do with android), i wouldn't mind giving you a little something for your time/knowledge.

---

### Post by oldfred on 2012-03-17
Glad you got it working. 

We are all volunteers here, and it is a pay it forward model. when you have learned something about Ubuntu then you can help those who know less.

---

