---
title: "Trying to fix boot problems, need some help with GParted"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by Number703 on 2014-05-10
I dual boot with Ubuntu and Windows 8. I recently upgraded to 14.04, and am unable to boot (even into Windows) the normal way, when I turn my computer on it just comes up with a grub error message. I am still able to get in through the BiOS/UEFI boot options menu, but I'd still like to fix this so I can just boot my computer and log in normally. I ran boot repair, which gave me this message: 
> 
[FONT=arial]An error occurred during the repair.[/FONT]
[FONT=arial]Please write on a paper the following URL:[/FONT]
[FONT=arial][http://paste.ubuntu.com/7369979/](http://paste.ubuntu.com/7369979/)[/FONT]
[FONT=arial]In case you still experience boot problem, indicate this URL to:[/FONT]
[FONT=arial][EMAIL="boot.repair@gmail.com"][COLOR=#222222]boot[/COLOR].repair@gmail.com[/EMAIL] [/FONT]
[FONT=arial]You can now reboot your computer.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))[/FONT]


Following Step 4 from [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition), the only partition that is at least 1GB and within the first 100GB of my disk is /dev/sda4, an ntfs partition. However, it has an error symbol next to it and I am unable to resize it. When I click it, it says > Unable to read the contents of this file system!Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.


For apt-get install ntfs-3g I get "ntfs-3g is already the newest version." For apt-get install ntfsprogs: 
> Package ntfsprogs is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'ntfsprogs' has no installation candidate

This is where I'm lost. Would I need to do something like an add-apt-repository for that? I found [http://www.ubuntuupdates.org/package/core/precise/universe/updates/ntfsprogs](http://www.ubuntuupdates.org/package/core/precise/universe/updates/ntfsprogs) for the package, but I don't know where to go from there, so any help would be appreciated thank you.

In case it's relevant, my boot flag is on /dev/sda2, fat32 file system, /boot/efi mount point.

---

### Post by oldfred on 2014-05-10
On April 12, 2011 it was announced that Ntfsprogs project was merged with NTFS-3G
[http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)
# Do not do install ntfsprogs as on newer versions it uninstalls ntfs-3g

Boot-Repair says Windows is hibernated. You have to turn fast boot off and keep it off. Windows will often turn both fast boot and secure boot on whenever you do Windows maintenance or updates.

You need to undo the Boot-Repair rename work around to boot Windows directly from UEFI menu. It renames the Windows boot file for those systems that have modified UEFI to only let you boot Windows. With the rename UEFI thinks it boots Windows but really boots grub/shim and then you only can boot the renamed Windows from grub menu not from UEFI.
      
 Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi


 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Grub will not boot hibernated Windows. You can fix Windows adn then redo the rename if your system will not boot Ubuntu any other way. Or you can try one of several other work arounds.

      
 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by Number703 on 2014-05-11
Secure boot is off, and I don't see anything called "Fast Boot." As for the rest of the post... I got a little lost in that. Could you give me a little step-by-step of what to do? 

> To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. Is that the first step then, run Boot-Repair again with that option ticked? What about > Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.? I'm confused as to whether I should or should not be running Boot Repair and what I should do in it, or if I need to do something before Boot Repair. 

Also: I am unable to get to Windows even from the UEFI menu now, I was able to do it before the Boot-Repair but now it looks like it's giving me the same error as when I try to boot normally, "error: Symbol 'grub_term_highlight_color' not found, with another line for "grub rescue>" where I can input text. Ubuntu and Mint still boot fine from UEFI. Windows boots on the /sda2 partition with the boot flag, Ubuntu I think is on /sda6 and Mint is on /sda10. I do remember when I first installed Ubuntu I had the same problem mentioned in one of the threads you linked, where it would just automatically boot into Windows, I think that was solved by putting the boot flag on /sda2 (and possibly doing some other things).

---

### Post by oldfred on 2014-05-11
Boot into Boot-Repair and run the restore backups. That should then get you booting back into Windows directly from UEFI menu.
Boot-Repair renamed the UEFI boot entry for Windows to boot grub/shim directly. Some computers will only boot Windows as the vendor modified UEFI.
If you can boot ubuntu entry directly that will resolve the Windows boot issue and you never should run rename as your UEFI does let you boot other systems.

Do not move boot flag around with UEFI/gpt. The boot flag is just a gparted convention to set which partition is the efi partition and that is the only bootable partition in UEFI. It is not the same as a boot flag in BIOS/MBR where that is the bootable Windows partition.

Is one of your installs an upgrade? This related mostly to those who upgraded.
 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

---

### Post by Number703 on 2014-05-11
Yes, this happened after I upgraded to 14.04. 
> You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.
Just so I'm clear, you mean for "sudo grub-install --recheck /dev/sdx" I should change it to "sudo dpkg-reconfigure grub-pc --recheck /dev/sdx"? And should I still run the boot repair or just try this first? I haven't done anything yet, I wanted to make sure I get everything straight before I go muddling around with this. Thanks for your help with this.

---

### Post by sandyd on 2014-05-11
> **Number703 said:**
> Secure boot is off, and I don't see anything called "Fast Boot." As for the rest of the post... I got a little lost in that. Could you give me a little step-by-step of what to do? 

Is that the first step then, run Boot-Repair again with that option ticked? What about ? I'm confused as to whether I should or should not be running Boot Repair and what I should do in it, or if I need to do something before Boot Repair. 

Also: I am unable to get to Windows even from the UEFI menu now, I was able to do it before the Boot-Repair but now it looks like it's giving me the same error as when I try to boot normally, "error: Symbol 'grub_term_highlight_color' not found, with another line for "grub rescue>" where I can input text. Ubuntu and Mint still boot fine from UEFI. Windows boots on the /sda2 partition with the boot flag, Ubuntu I think is on /sda6 and Mint is on /sda10. I do remember when I first installed Ubuntu I had the same problem mentioned in one of the threads you linked, where it would just automatically boot into Windows, I think that was solved by putting the boot flag on /sda2 (and possibly doing some other things).

Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by Number703 on 2014-05-12
I can't get into Windows 8 right now, so no control panel. 
As for the grub_term_highlight_color error: 
sudo dpkg-reconfigure grub-pc --recheck /dev/sdx yields:> Unknown option: recheck
Usage: dpkg-reconfigure [options] packages
  -a,  --all			Reconfigure all packages.
  -u,  --unseen-only		Show only not yet seen questions.
       --default-priority	Use default priority instead of low.
       --force			Force reconfiguration of broken packages.
       --no-reload		Do not reload templates. (Use with caution.)
  -f,  --frontend		Specify debconf frontend to use.
  -p,  --priority		Specify minimum priority question to show.
       --terse			Enable terse mode.
Just running sudo dpkg-reconfigure grub-pc yields
> dpkg-query: package 'grub-pc' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub-pc is not installed


Should I try with grub-install? It also seems like there are a few different codes people are putting out there on that post, like "sudo grub-install --boot-directory=/mnt/<sth>/boot /dev/sdX" Should I try any of those? Would I switch the /dev/sdX to /dev/sda2 since that's my boot partition? I don't want to just start doing trial and error with this in case I mess something up.

---

### Post by squakie on 2014-05-13
First do what oldfred said to restore the files using boot repair.  That should allow you to boot Windows.  Then while in Windows, follow SandyD's post for fast boot.  Then completely shutdown Windows (don't hibernate).  I believe then you should be able to boot the boot repair disk and run it and it should run correctly, after which when you reboot you get the boot menu.

---

### Post by Number703 on 2014-05-14
Okay, well, I guess I made some progress. I restored the files and disabled fast boot, then ran boot repair. Currently, the 'grub_term_highlight_error' message is gone and I am able to boot into Windows 8 from startup, but am still only able to get into Ubuntu by going through the UEFI options. Boot Repair gave me the same error as when I started, although at least this time there's no error next to /dev/sda4, so I could resize it this time. I added a new ext4 partition before /sda4 (so it is within the first 100GB), the new partition is /sda12, ~1.5GB. However, I am still unable to get everything working. I get stuck at step 6 on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition). "[COLOR=#333333][FONT=Ubuntu]- Tick the [/FONT][/COLOR]**"Separate /boot partition: sdXY"**[COLOR=#333333][FONT=Ubuntu] option (sdXY must be your 1GB partition)." Under GRUB Location, "separate /boot partition:" is grayed out and unticked. The pulldown menu next to it is /sda11, which is right after the sda4 partition (I created it right before /sda12, accidentally added it after the /sda4 instead of before it). According to the steps, I need to tick this and select /sda12, but I cannot tick it because it is grayed out. There is another option below it, "Separate /boot/efi partition:" with sda2 as the only available option. It is ticked, but even unticking it does not allow me to tick the "Separate /boot partition" option. So, any ideas?

Here is the boot repair log from the most recent boot repair, which I conducted after disabling fast boot. [/FONT][/COLOR][http://paste.ubuntu.com/7460239/](http://paste.ubuntu.com/7460239/)

---

### Post by oldfred on 2014-05-14
I have not yet seen a UEFI system where the far from start of disk was a real issue. It does happen with some BIOS based systems, particularly USB installs.
Often adding a separate /boot just complicates install, and maintenance as you have to remember to mount it whenever fixing system and have to make sure it does not fill with old kernels.

Most HPs have modified UEFI to only boot Windows. Or boot automatically.
[SIZE=1]
[/SIZE][SIZE=1] [FONT=arial]**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**[/FONT][/SIZE]
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   If Description has to be Windows then change description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by Number703 on 2014-05-14
Okay, well that's the error boot-repair keeps giving me so then I have no idea what the problem is if it's not that. Could you explain what the rest of your post is? It seems like a lot of jargon and a lot of links, not really sure what I should be doing at this point to get it to boot back into the boot menu instead of automatically going to Windows 8 every time. I had this same problem when I first installed Ubuntu on this machine. I solved it then by removing a second bootflag on /sda5, running boot-repair, and running efibootmgr -c. There is no second boot flag to remove, boot-repair isn't doing anything, and if it helps the output from efibootmgr -c is: 
> BootCurrent: 0000Timeout: 0 seconds
BootOrder: 0003,3001,3000,3002,3004,2001,2002,2003
Boot0000* ubuntu
Boot0001* Windows Boot Manager
Boot0002* linuxmint
Boot0004* Ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk
Boot0003* Linux


---

### Post by oldfred on 2014-05-14
You are showing a variety of bootable systems. But many with HP have posted that they could not set anything but Windows as the default.
Each of those is an alternative way to work around the UEFI only boots Windows issues.

I am not sure I like the Boot-Repairs rename of the Windows efi boot file. Some manually rename bootx64.efi and set drive as default and that works. You then can still directly boot Windows from UEFI menu, where Boot-Repairs rename only lets you boot Windows from grub menu.

Some like the rEFInd as that is a graphical boot manager, but icons to choose what to boot. It started with Mac as that started using UEFI long before Windows. But it is something else to install and configure.

---

### Post by Number703 on 2014-05-16
Huh. Well, that might be something I'll look into in the future. But I've already spent quite a bit of time trying to fix this (and have several other tech issues I need to work on), so I think I'm just going to stick with booting up from the UEFI menu for now. Thanks for the help, at least I can boot into Windows if need be.

---

