---
title: "How to eliminate one OS from a triple boot drive"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by ineuw on 2012-07-27
I have a triple boot desktop with Xubuntu 12.04, Win7 trial copy, and Win XP SP3. Since the Win7 30 day trial expired, I want to erase it, but don't know the correct procedure how to point Grub to boot into Win XP directly so that I can safely reformat the Win7 partition.

On boot, Grub lists the Win7 loader, which in turn lists Win XP as the older OS. I am concerned that the reformat of the Win7 partition will also affect the Win7 loader which gives me access to Win XP.

sda is dedicated to the three OS and contains no data. It is configured as follows:

sda1 = Win XP SP3
sda4 = swap
sda5 = Win 7 SP1
sda6 = Xubuntu 12.04

I have GParted 0.11.0 and Grub Customizer 2.5.7 installed. Can someone in the know please advise? Thanks.

---

### Post by Bufeu on 2012-07-27
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by NikTh on 2012-07-27
Hi , 
here its an automatic and easy tool to do your job --> [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

Thanks

---

### Post by oldfred on 2012-07-27
Which partition has the boot flag. Windows only boots from the active partition or the one with the boot flag. It literally then moves all the boot files from additional installs into the boot flagged partition.

If XP was first it probably was the one with the boot flag. But you have both the XP boot files & the Windows 7 boot files. Then you can just delete/reformat Windows 7 partition.
But, it may have converted NTFS boot sector to boot Windows 7, so you may have to repair the NTFS boot sector. I used a Windows 7 USB to run chkdsk on my XP and it did work better than the XP version. But it converted Boot Sector to Windows 7 spelling out booting with bootmgr not ntldr. But I found instructions to repair boot sector. 
If you can still make a Windows 7 repairCD or USB I would.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by ineuw on 2012-07-27
My sincere thanks to everyone. Each reply provided an answer to the many questions I had. I will return to this post after completion to report the process used.

---

### Post by ineuw on 2012-07-28
Can someone please mark this as solved? Thanks.

Many thanks for all the advice given. It added to my hazy knowledge but it was up to me to sort out, try, and eliminate non-working options.

svg000's comment was the clue which confirmed my suspicion that the Win7 boot loader cannot be eliminated and rebuild XP boot from Ubuntu. 

I used the XP install CD to boot into the recovery command prompt and use FIXBOOT to overwrite the Win7 loader and re-access XP. Then, I used the Xubuntu live CD to fix Grub2 to boot into Ubuntu.

In Ubuntu, Boot-repair was used to purge and rebuild Grub2, and then used Grub Customizer to set the preferred default OS to boot.

------

Comments:

In the XP recovery console, FIXMBR repairs the XP boot but doesn't eliminate the Win7 boot loader.

After fixing the XP boot, in Ubuntu, editing the 30_os-loader and adding Win XP info manually, then updating Grub2 (either with Grub Customizer or Boot Repair) fails because the examples of the code and the procedure on the web are, either out of date, or missing crucial information for an ignorant newbie.

After removing the Win7 boot loader, if no partition change is planned, it's preferable to reformat the old Win7 OS partition from Windows instead of using Gparted from Ubuntu. Doing it from Ubuntu it is more work. 

Hiren s-Boot-cd would have been a great tool but it was posted after I fixed everything.

------

The following are the recommended steps to remove Win7, where the order of OS installation was 1 = XP, 2 = Win7, 3 = Ubuntu 12.04:

1. Use any Windows boot utility CD to fix the Windows XP boot record. Reboot to see if XP is accessed correctly. Boot.ini may need modifying through the Control panel\System\Advanced options.

2. Use (X)ubuntu live CD to repair grub2 to boot into (X)ubuntu.

3. Use Boot-repair to rebuild Grub2 and reboot to test.

4. Use Grub Customizer to set the desired boot order & default. Reboot to test.

4. Use GParted to manage the freed Win7 partition to resize, or reformat. Reboot to test for boot time mount errors. This can be corrected if needed with ntfs-config.

I hope this helps others.

This is also posted to LinuxQuestions.org

---

