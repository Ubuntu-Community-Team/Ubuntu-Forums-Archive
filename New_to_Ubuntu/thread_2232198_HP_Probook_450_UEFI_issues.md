---
title: "HP Probook 450 UEFI issues"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by tranbaolog on 2014-06-30
Hey guys, I'm new. I'm having trouble here. And since I really have no clue what is what, I'm gonna describe everything with as much details as I possibly can. 


I have a HP laptop with UEFI. (HP Probook 450 g0 to be exact.)


I got windows 8.1 installed first.


Installed Ubuntu 14.04 second, following guides on the internet. I think I installed it correctly, with secureboot and fastboot and disk partitioning all configured right. I could boot to both windows and ubuntu at this time. 

If I turn on my laptop and do nothing it would went directly into windows.

If I press Esc right after powering up, when there is a screen with the HP logo in the center and a small line says "Press ESC for more option" at the bottom-left of the screen (you know that kind of screen you got right after you press the power button), then it would show me a menu. Then I would press F9 for Choose boot option (I don't remember the exact words, but it doesn't matter right?). A list showed up, it has the same look as the BIOS setting (or should I say EFI setting!?). Then I could use arrows to choose which "device" to boot from. It has Bootable USB (if connected), Windows, ubuntu and a bunch of other things. Then I can choose Ubuntu and GRUB2 would show up, or I can choose Windows, and everything works alright. 

Decided that I want my laptop to boot to ubuntu first instead of windows. Like I only have to press power and wait for ubuntu to turn up, not having to press ESC > press F9.. like that.

After some Googling (not enough though) I ended up with easyBCD (I know, trouble maker here). I followed some guide and changed something. Unfortunately I cannot remember what I did.

After that when I try to boot to **windows**, which is still the default boot, I got a black error screen saying Windows can't start because of of "BCD file does not contain valid info for an OS", error code: 0xc0000098.
Here's a picture I found on the Internet, mine looks the same: 
[IMG]http://www.prime-expert.com/articles/b18/images/boot_error_status_0xC0000098.png[/IMG]

Then when I press ESC again to go back to the EFI menu and choose to boot from Ubuntu, it still works fine. I'm in ubuntu right now.

Asked Google sensei again. This time I tried boot-repair to fix the problem.

**Didn't work.**

But it certainly did changed something, as I notice some differences in the booting process. 

Right now:
> Power button
> Esc
> F9
> there are FIVE 'ubuntu' lines on the list, before there was only one. Choosing any of those would work the same.
> GRUB2 shows up. There are: ubuntu, advanced options for ubuntu, Win bootmanager, windows-UEFI-something, windows-something again, a bunch of HP/Efi/... or something like that.
> choosing any windows-something option would result in the same black error screen as described above.
> choose ubuntu. works well.

Here's my boot info: [http://paste.ubuntu.com/7721488/](http://paste.ubuntu.com/7721488/)

Here's a screenshot of GParted:
 [IMG]http://i.imgur.com/rOcVMpk.png[/IMG]


[SIZE=3]**>> Question 1: **[/SIZE]How can I fix this. I really believe that it's only because of some files and that should be easy to fix. But I have no idea how.

[SIZE=3]**>> Question 2: **[/SIZE]In case the problem was hard to fix, **Could I just simply format the disk partitions that contain windows and windows recovery **(namely sda1, sda3, sda4, sda5 on my computer, please see screenshot above) and then **re-run boot-repair** or something to get single Ubuntu working? I mean to 'uninstall' windows in the forcing way and **get ubuntu as the only OS**? Will that be alright?



// PS:
I just found this thread. I think I have almost identical problem with this guy. The differences being:
1. He had Win7 + Ubuntu 12.04. I have WIn8.1 + Ubuntu 14.04
2. He had important stuff on Win 7. I don't.
[http://ubuntuforums.org/showthread.php?t=2073283](http://ubuntuforums.org/showthread.php?t=2073283)

---

### Post by oldfred on 2014-06-30
Moved to your own thread. 
Tutorials thread is for only posting issues or new/added instructions to tutorial.

Please use advanced editor and paperclip icon to attach screenshots. Inline pictures may cause issues for those users with slow Internet.

Not sure internally what HP does, but it seems to be one of those that only boot Windows. Boot-Repair has renamed the Windows boot entry to be actually grub/shim. So UEFI thinks it boots Windows but really boots grub.

You have done choice b: below. 
You may have to undo  that with Boot-Repair and see if you can direclty boot into Windows from UEFI menu entry. And you may need to use f8 to get into repair mode. You should make a Windows repair flash drive so you can fix Windows as grub really only boots working Windows.

       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming shimx64.efi or grubx64.efi to be  /EFI/Boot/bootx64.efi (back up originalbootx64.efi)
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by tranbaolog on 2014-06-30
Thank you for your help.

Right now I cannot boot to windows AT ALL, whether from GRUB or UEFI. Both ways ended up showing the black screen above. And as of right now I only wish to have windows back. The whole "which boot first" thing can wait ;). Or maybe I can format all the partitions that contain windows files, and then "clean up" GRUB and UEFI later somehow? I could install a fresh windows and then a fresh ubuntu all over again if I must. 

And btw all the boot info is stored in the sda2 (see picture above) right? So even if I format sda1, sda3, sda4 and sad5 everything that happen during the boot process will still be the same, is that true?
 
I believe it was easyBCD that caused the problem in the first place, since it was broken after I messed with it to set ubuntu as the default boot option. So boot-repair, if anything, only worsen the situation.

How about using a liveUSB containing the windows.iso file that I used to install windows to repair it? Since in the post above someone mentioned that changing filename would be reset after a windows update.

---

### Post by oldfred on 2014-06-30
To directly boot Windows in UEFI menu change it back with Boot-Repair.
       Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

then you may need to use f8 to get into Windows repairs.
Or you may need your Windows repair console from a Windows repair flash drive or a third party repair tool.
With UEFI you should never need EasyBCD, but it does repair BCDs if that is the issue.
      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)
These also may have some repair tools for Windows.
   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

Best to have your own repair flash drive.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

