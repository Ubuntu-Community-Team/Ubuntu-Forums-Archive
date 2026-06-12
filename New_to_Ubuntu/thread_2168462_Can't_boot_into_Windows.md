---
title: "Can't boot into Windows"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by joshua6 on 2013-08-17
I installed Ubuntu alongside Windows 8 on my pc last night and it was all going well until I messed up the Windows boot path while trying to fix up the boot loader with Easy BCD. I can boot into Ubuntu, but if I try to boot into windows all I get is a blank screen and nothing will happen. I can get to the Windows 8 recovery options, but none of them are any help, I even tried system restore. I really don't want to reinstall windows if at all possible. I need to know if there is any way to fix Windows to boot up. I ran Boot Repai on Ubuntu, and here is the output thing [http://paste.ubuntu.com/5998069/](http://paste.ubuntu.com/5998069/)

Any help would be greatly appreciated, as I need to be able to boot Windows Monday for school.

---

### Post by Andy_Browning on 2013-08-18
If you go into your Windows partition from the Ubuntu side do you see all your files and folders where they should be?
If so, you could try the check disk utility program in the mini XP OS in the Hirens boot CD to correct the Windows boot sector.
Worked for me when I messed up my Windows boot sector with a hung install of Lubuntu (forgot to check the md5 sum of the downloaded iso).

---

### Post by westie457 on 2013-08-18
Hi Joshua6, welcome to the Forum.

At the moment the only way to get Windows to start is via the one-time Boot Menu at computer start up. The key to press is usually F12 (check the manual for the correct key) press this immediately after power on release when you see the message 'please wait' on the screen.
Here you will get a list of the available boot-options. You might have 2 or more listings for Windows. Choose one, if Windows does not start repeat the process working down the list until Windows starts.

When you have Windows running go to the Control Panel > Power options and disable 'Fast Boot' and for good measure disable hibernation/suspend. Save the changes exit the the screens and shut down Windows.

Boot into Ubuntu and run 'Boot-repair' again. The default options should now repair as necessary and install properly and allow you to boot whichever OS you choose.

Any problems post the link to the new Bootinfo Script and we will have another go.

Hope this helps.

---

### Post by joshua6 on 2013-08-18
Hey guys, thanks for the replies. When secure boot is disabled, it loads GRUB which gives me numerous windows options, but none of them work except the one for the recovery menu, which still won't boot Windows. On some of the options, such as the "Windows 8 loader" give me an error that the EFI is invalid. the other options bring me to windows boot manager which gives me one choice: "Microsoft Windows 8", and if I click it I get that same black screen, and nothing loads.I had already disabled fast boot in Windows before this happened. I'm pretty sure what I did was give Windows Boot Manager the wrong address to boot windows from, and thus it boots nothing but a black screen.
Edit: I pressed F12 at boot, and it brought me to Windows Boot Manager, which still only gave me the one option of "Microsoft Windows 8", which gives me the blank screen and loads nothing.
If I could just get back to Easy BCD I could fix it(or so I believe), but I can't get WINE to work.

---

### Post by oldfred on 2013-08-18
With UEFI you do not need EasyBCD to boot. But, it may also help in fixing BCD issues.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
Some default Windows boot entries in grub menu will never work as those are old BIOS type entries.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by joshua6 on 2013-08-18
Here is the Boot Info Report: [http://paste.ubuntu.com/6000334/](http://paste.ubuntu.com/6000334/)
I clicked the link you posted about UEFI boot from GRUB, but I don't get how to fix it. If I can get Windows booted just once from GRUB I can fix it, but I don't understand how to do any of the fixes when I have searched the "Invalid EFI path" error on google.

---

### Post by oldfred on 2013-08-18
this is your menu entry that will work.

>  menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 303F-DAAD
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}



But if you left fast boot on or resized Windows with the installer so it needs chkdsk, you need to directly boot from UEFI and see if you can repair it. Often from grub, you cannot get to the Windows repair console with f8.

---

### Post by joshua6 on 2013-08-18
I tried that option, but it brought me to Windows boot manager, and every time I select windows 8( the only option) it just loops back to windows boot manager. I went into recovery mode and ran chkdsk, and it found errors immediately, but it wong let me run chkdsk /F (to fix the errors) because it says the volume is write protected.

---

### Post by oldfred on 2013-08-18
I do not know Windows 8.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

If you have access to another Windows 8 system you can make a repair flash drive.
      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Otherwise.

 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by joshua6 on 2013-08-18
I finally got it! I had replaced the UEFI boot path with a BIOS one. What I had to do was go to the Windows recovery menu that I could still get open, run the command promt, and run "bcdboot C:\Windows" It regenerated the boot path and now I'm posting this from windows. Thanks you all for your help, especially oldfred! Now that I'm back to normal, hopefully I can get a full grasp on everything that Ubuntu has to offer(I only have one other installation of it, an old desktop that I rarely use).
Once again, thank you very much for your assistance.

---

