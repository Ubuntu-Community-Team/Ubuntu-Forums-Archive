---
title: "win 8/ubuntu boot"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by ray9 on 2014-10-02
So I got a laptop (HP) with win 8 and installed ubuntu 14.04LTS.  Don't use it very much.  But now I I'm using it more and is there an easier way to get into ubuntu that booting into win8 then going to settings and UEMI or whatever it is to find the bios settings?  I had it booting using boot repair at one time but it isn't working anymore.  Win 8 decided it wouldn't connect anymore too.
Is there a way to erase win 8 and leave ubuntu on the drive?

Thanks in advance

---

### Post by oldfred on 2014-10-02
We regularly get users who erase Windows and then find that one application or game they really need or want only runs in Windows and want to dual boot. But they did not backup Windows and totally erased any recovery partitions on hard drive. 

Best to fully backup Windows & efi partition.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

You could also shrink the Windows NTFS partition a lot, but for Window to run well, it does need 30% free inside the NTFS partition. At 10% free you just about cannot run defrag as it does not have any working room to copy files back & forth.

HPs have made it a bit more difficult to directly boot Ubuntu. They have modified UEFI to only directly boot Windows or the hard drive.
But some of the work arounds are to rename files, so system still thinks it is booting Windows or hard drive, but really loads grub. Renaming Windows efi boot file, while it works can lead to issues later with Windows update overwriting the grub file. And then you are back to only booting Windows.

Many with HP have renamed the hard drive boot /EFI/Boot/ entry:

  Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Some other HP and various work arounds or issues they had.

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by ray9 on 2014-10-02
Thanks you so much for all the information.  I finally got it to connect and will get on the info you provided.

---

