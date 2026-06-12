---
title: "Windows XP fails to Boot After Backup (Ubuntu 13.10 - Windows XP)"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by byrondallas on 2014-04-02
Hi guys. I'm dual booting Ubuntu 13.10 and Windows XP. The other day I needed to restore my laptop from an image backup. Everything seemed to go fine until I tried to boot into Windows XP from the boot menu. All it gives me is a black screen with the cursor blinking. I'm still able to boot into Ubuntu and it works fine. I can even see my Windows partition from my Ubuntu file manager. I tried running the boot repair disc but it actually removes the Windows option from the boot menu screen. I also tried booting up the Windows XP recovery tool and running fixboot and fixmbr, but no luck. Also tried booting from a Ubuntu live CD to repair grub:


[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UzyBpPldWSp](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UzyBpPldWSp)


Still no luck. The only think that works for me is to use a repair boot cd and windows boots up fine with everything working.


[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)


Now I don't know if this matters but it's better give too much info than not enough. My Windows XP partition is FAT32 and Ubuntu is ext4. The backup drive is NTFS. I don't know if that creates a problem when backing up two partitions with different formats to one hard drive? You can see my partitions here:


[https://www.dropbox.com/s/t6dnzjbs4o5qkva/gparted.png](https://www.dropbox.com/s/t6dnzjbs4o5qkva/gparted.png)


Sorry for the long post but I tried everything before coming here. I'd really like to figure this out so I can rely on my backups. Just like to add that when the backup was made, both OS booted fine.

---

### Post by monkeybrain20122 on 2014-04-02
Maybe MS killed it. :) Seriously why are you still running XP, just save your data and wipe it out. Also I am not sure how do you install Windows in FAT32 to begin with, FAT can only handle 4G of contents.But then I don't use Windows.

---

### Post by byrondallas on 2014-04-02
It's an old laptop that came with Windows XP. I use it to experiment with and to try programs on before I decide to install them on my main Windows 7 machine.

A little about Windows XP and Fat32:

[http://support.microsoft.com/kb/310525](http://support.microsoft.com/kb/310525)

---

### Post by Mark Phelps on 2014-04-02
Depends on HOW you do your backups ...

I do Windows backups using Macrium Reflect (in Windows) to a shared NTFS partition.

I do Linux backups using Clonezilla to a shared Ext4 partition.

In the past, I have done Clonezilla backups (from a Clonezilla LiveCD) to NTFS partitions, as well.  That works because the backup is an image file and the individual folder and file partitions used in the Linux filesystem are contained INSIDE the image file, so the fact that the image backups are not on a Linux filesystem is not a problem.

---

### Post by byrondallas on 2014-04-02
I use this backup program here:

[http://www.nticorp.com/en/us/product/nti-backup-now-ez-3.asp](http://www.nticorp.com/en/us/product/nti-backup-now-ez-3.asp)

And it backs up Windows and Ubuntu on the same image file. What you see here is what's on the image backup:

[https://www.dropbox.com/s/t6dnzjbs4o5qkva/gparted.png](https://www.dropbox.com/s/t6dnzjbs4o5qkva/gparted.png)

---

### Post by byrondallas on 2014-04-02
To be more specific, these are the backup files:

[https://www.dropbox.com/s/ruk77x5uzhah7f1/backup.PNG](https://www.dropbox.com/s/ruk77x5uzhah7f1/backup.PNG)

---

### Post by LostFarmer on 2014-04-02
> The only think that works for me is to use a repair boot cd and windows boots up fine with everything working.  Might help us help you if you tell us just what do you do with the hirens repair boot cd to get XP to boot .  

>  I tried running the boot repair disc but it actually removes the Windows option from the boot menu screen What boot repair disk and just what do you do with it ?

>  I also tried booting up the Windows XP recovery tool and running fixboot and fixmbr, but no luck.  No luck running the commands or did the commands run with no errors but the problem was not fixed ?

Many different things could be the problem, so we need as much information that you can give.

---

### Post by byrondallas on 2014-04-03
When I install the hirens repair boot cd, it opens up and the top option is "Boot from Hard Drive" and Windows opens up right away.

This is the boot repair I've been using and I select recommended. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What's strange is that when I go into the advanced settings, it's showing Windows XP, but after it runs and I reboot, windows boot option is missing. I've tried this 2 or 3 times with the same results.

With the Windows XP recovery tool, the commands ([COLOR=#000000]*fixboot and fixmbr) *[/COLOR]executed just fine with no errors. But after rebooting I'm still not able to boot into Windows from the boot screen.

---

### Post by LostFarmer on 2014-04-03
> When I install the hirens repair boot cd, it opens up and the top option  is "Boot from Hard Drive" and Windows opens up right away.
 I have no idea just how 'Boot from Hard Drive works.  Does it boot directly into XP or into grub and you select XP ?  When you reboot does it work correcly ?

when you run>  Boot-Repair, 

[LIST]
[*]Then click the "Recommended repair" button. When repair is finished, note the URL (**paste.ubuntu.com/XXXXX**) that appeared on a paper, then reboot and check if you recovered access to your OSs.  


[*]If the repair did not succeed, indicate the URL to people who help you by email or forum. 
[/LIST]
  can you post the URL.

Just to let you know, as of let I have no clue of problem but thinking it might be a grub problem for some reason.

---

### Post by byrondallas on 2014-04-03
When I boot from [COLOR=#000000][I]hirens repair boot cd, it boots directly into Windows, no grub.

Here's a summary before clicking "Recommended Repair":
[/I][/COLOR][http://paste.ubuntu.com/7198854/](http://paste.ubuntu.com/7198854/)

Here's a summary after repair:
[http://paste.ubuntu.com/7198873/](http://paste.ubuntu.com/7198873/)

No the boot repair did not succeed. After repair I lost the option to choose Windows but gained about 4 memory test options.

---

### Post by LostFarmer on 2014-04-03
boot normaly and when you get to the grub menu- press 'C' to get into the grub command prompt and enter
```
insmod part_msdos
insmod fat
set root='hd0,msdos1'
chainloader +1
boot
``` does that boot into XP ?


looking at the pastebin for your grub.cfg , there is an entry near the top that *I do not think* should be there and might be causing a problem with 'update-grub' command.  looks like it comes from /etc/grub.d/00_header .   Do you remember editing that file ?  Take a look at ' /etc/grub.d/00_header'  , near the top and see if it is there.
```
set default="menuentry 'Microsoft Windows XP Home Edition (on /dev/sda1)' --class windows --class os  'osprober-chain-320D-180E' {"

```  

'320D-180E' is being used as the XP partition's UUID and it is now wrong as per 'blkid' output of```
/dev/sda1        533D-2B0C                              vfat       ACER
``` 

If one wants to manuaily enter a boot menu it should be place in '/etc/grub.d/xx_custom' not in ' /00_header', and then run  'update-grub'.

---

### Post by byrondallas on 2014-04-04
Just so you know,  I'm back to the original boot loader (complete system restore from backup) since the repair didn't work:


[http://paste.ubuntu.com/7198854/](http://paste.ubuntu.com/7198854/)



When I enter:


```
insmod part_msdos
insmod fat
set root='hd0,msdos1'
chainloader +1
boot
```


from the boot menu command prompt,  it takes me to a black screen with the cursor blinking. 

No I've never edited the /etc/grub.d/00_header. Here's the contents of that file:

[http://paste.ubuntu.com/7203296/](http://paste.ubuntu.com/7203296/)

Also something I failed to mention with the original boot loader,  when I choose Windows XP I get this error:

error: no such device: 320D-180E

---

### Post by LostFarmer on 2014-04-05
Had to do some testing on my old comp with XP (fat32) and linux to test a idea of problem. I do not understand why its a problem but it seems to be one of your problems.

The quotes will be from your Boot-Repair info.

> sda1: __________________________________________________________________________

File system: vfat
Boot sector type: Windows XP: FAT32
Boot sector info: According to the info in the boot sector, sda1 starts
at sector [COLOR=#ff0000]63[/COLOR]. But according to the info from fdisk,
sda1 starts at sector [COLOR=#008000]2048[/COLOR]. 
Operating System: Windows XP
Boot files: /boot.ini /ntldr /NTDETECT.COM
> /dev/sda1 * [COLOR=#00ff00]2,048[/COLOR] 184,113,151 184,111,104 c W95 FAT32 (LBA)
> =================== hexdump -n512 -C /dev/sda1
00000000 eb 58 90 4d 53 57 49 4e 34 2e 31 00 02 20 06 00 |.X.MSWIN4.1.. ..|
00000010 02 00 00 00 00 f8 00 00 3f 00 ff 00 [COLOR=#ff0000]3f 00 00 00[/COLOR] |........?...?...|

'3f 00 00 00' hex=63 decimal.

Your XP was installed in a partition that started at sector [COLOR=#ff0000]63[/COLOR] but I would say your backup program installed the partition starting at sector [COLOR=#00ff00]2048[/COLOR]. XP does not care but grub seems to care.

The 'hexdump /dev/sda1' is of the Volume Boot Record 'VBR' , the part in red is called 'Hidden Sectors', the sector count from the MBR to the VBR.

On my setup I changed that value and had the same problem as you do. On may setup I use 'plop' in the MBR and have grub in the linux partition. Using plop to boot XP, just resulted in a reboot, grub would just give me a blank blinking cursor. Hirens repair boot cd, had no problems booting XP.

Try editing the VBR (can use 'dd' to copy the VBR into a file and then edit file with 'bless hex editor' then writting the edited file to the VBR) or you can boot into XP via Hirens boot cd and use MS's 'diskprob'. Edit it to look like "NEW hexdump" below.

===================  NEW hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 06 00  |.X.MSWIN4.1.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 [COLOR=#0000ff]00 08 00 00[/COLOR]  |........?...?...|[/CODE] '00 08 00 00' hex =2048 decimal.

Then run 'update-grub' , check /boot/grub/boot.cfg to see if XP is listed or just try rebooting into XP.

Instead of the above, might see if your restore program will let you select the partition to start at sector 63 vice sector 2048.

You may also have a problem with XP's UUID.  If after you do the above , grub still gives you 'error: no such device: 320D-180E ' , try the grub boot command I gave before.

---

### Post by byrondallas on 2014-04-06
> **LostFarmer said:**
> or you can boot into XP via Hirens boot cd and use MS's 'diskprob'. Edit it to look like "NEW hexdump" below.

===================  NEW hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 06 00  |.X.MSWIN4.1.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 [COLOR=#0000ff]00 08 00 00[/COLOR]  |........?...?...|[/CODE] '00 08 00 00' hex =2048 decimal.


Ok I have Disk Probe on my Windows XP but I've never used it. Can you go a little more into the details of what your telling me?

---

### Post by oldfred on 2014-04-06
Actually just running chkdsk several times should fix the issue.

All Windows NTFS partitions must have inside the PBR or partition boot sector the same partition start & size info as the partition table. As LostFarmer pointed out they do not match.
And normally after any resize of a NTFS partition, you have to run chkdsk to update PBR with new size info.

Grub can only boot a working Windows so if Windows did not boot with a Windows boot loader, grub will not be able to chainload to Windows and boot it.

---

### Post by byrondallas on 2014-04-06
> **oldfred said:**
> Actually just running chkdsk several times should fix the issue.

And then would I need to update-grub?

Also would running windows xp [COLOR=#000000]recovery tool and running fixboot and fixmbr do the same thing?[/COLOR]

---

### Post by oldfred on 2014-04-06
The fixboot may do something similar, but chkdsk should do it. Often you have to run the full set of Windows repairs to fix everything as it may not be clear which is the issue. 

You can run fixMBR if you want to test that Windows does boot. Then once Windows is working reinstall grub to MBR.

---

### Post by byrondallas on 2014-04-07
Okay I've run chkdsk 4 times and Windows still fails to boot from the boot menu. I can run fixboot and this error goes away ([COLOR=#000000]error: no such device: 320D-180E) but it still takes me to a black screen with the cursor blinking. If I run fixmbr how do I reinstall grub to MBR again?[/COLOR]

---

### Post by oldfred on 2014-04-07
You will need Ubuntu live installer DVD or flash or other Linux repairCD.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Or just use Boot-Repair.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by byrondallas on 2014-04-07
If after running fixboot and fixmbr, should I be able to boot into windows? I've run both of those commands and now when I boot up my laptop I'm only seeing a blank screen with the blinking cursor.

---

### Post by oldfred on 2014-04-07
Not sure where you are at. 
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by byrondallas on 2014-04-08
After running chkdsk several times from a complete backup, I still got this error after trying to boot windows from the boot menu, ([COLOR=#000000]error: no such device: 320D-180E). So I loaded the Windows XP Recovery disk and ran fixboot and fixmbr. Now this is where I'm at presently. When I power up my laptop it just goes to a blank screen with a blinking cursor, no more boot menu. Here is a summary from boot repair without making any changes:

[/COLOR][http://paste.ubuntu.com/7221598/](http://paste.ubuntu.com/7221598/)

---

### Post by oldfred on 2014-04-08
If you are directly booting Windows that purely is a Windows error.

But this should have been fixed with the chkdsk.

>     Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda1 starts at sector 2048.



---

### Post by byrondallas on 2014-04-08
How many times should I need to run chkdsk? I've ran it 3 times already.

---

### Post by oldfred on 2014-04-08
That should be enough, generally you just need to run until no errors.

I have seen where the sector start and other internal MFT data overlap and chkdsk just keeps switching error back and forth. Did have in that case see an error and user just reinstalled.

You might want to try to change partition to the old start of 63 as that is what XP always used. It is new partition tools that use 2048 for compatiblity with new 4K drives & SSDs. Then restore backup with that 63 start as that probably was the original.

I did find running chkdsk from a Windows 7 repair flash drive on XP worked better but it then converted boot sector to Windows 7 type and I had to also restore a XP type boot sector.
 Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later



You can also then try this, it can build a new boot sector that is XP type:
 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by byrondallas on 2014-04-08
> **oldfred said:**
> You can also then try this, it can build a new boot sector that is XP type:
 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

I think I'll try this later today since most of what your talking about is a little over my head. If this doesn't work I'm just going to go back to the laptop restore disks and start Windows XP from scratch. This is just a machine I experiment with anyway so it's not like I'm loosing any important files plus I could save them from booting from Hiren's repair disk if I needed to. Thanks guys for all of your help. It's REALLY appreciated. :)

---

