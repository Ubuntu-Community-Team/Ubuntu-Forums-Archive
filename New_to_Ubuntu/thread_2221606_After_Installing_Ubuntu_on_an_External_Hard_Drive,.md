---
title: "After Installing Ubuntu on an External Hard Drive, Receive &quot;error: no such device&quot;"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by eddy4 on 2014-05-02
Hello all,

I have a very urgent problem concerning my first-time install of Ubuntu. After installing Ubuntu 14.04 onto a new Ubuntu-installation-software-generated partition in my external hard drive, I followed the prompts, eventually leading me to removal the installation disk and rebooting my laptop. After waiting for a bit, instead of seeing anything Ubuntu or Windows 7-related screens... I see something similar to a command prompt, beginning with the phrase "error: no such device", with a string of text or coding after it. The next says: "grub rescue>". I have no clue what this is. 

At this point, I only have one goal: remove Ubuntu from my system and bring back Windows 7 with all my files and programs intact.

Regards,
Eddy

P.S. Even when I remove the external hard drive, the same thing appears.

---

### Post by chriswill2 on 2014-05-03
hmmm that strange, especially after you remove your external drive. Check your BIOS settings and see the boot option right there. Make sure that your laptop is booting from the internal drive

---

### Post by oldfred on 2014-05-03
If you used auto install option, it installs grub2's boot loader to sda which usually is the internal drive.
With a removeable drive you want grub2's boot loader in the MBR of the removeable drive and keep the Windows boot loader in the MBR of the internal drive. Then set BIOS to boot from external first. Grub should give you option to boot Ubuntu or Windows. With external removed BIOS will skip external and boot internal with just Windows.

If you tell Boot-Repair second drive is removeable it shoud fix you up. If not post the link it gives to it BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by eddy4 on 2014-05-03
I am currently trying to boot from the hard disk directly, but unfortunately it's not working. I just get stuck at a black screen after going into boot disk options and selecting the USB External Seagate Hard Drive.

(I should mention that HP Elitebooks have their own BIOS Menus that are essentially a "dumbed down" and more aesthetically pleasing version of the normal Windows 7 BIOS.)

---

### Post by oldfred on 2014-05-03
Black screen is usually a video issue.
What video chip? Usually Intel just works.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by eddy4 on 2014-05-03
It's a black screen, but I can tell that the screen is on by the "dark backlight" that indicates a black screen that is purposely shown by the monitor / laptop screen. My video card is the one that comes with the Intel i5-2450M (my laptop's processor), the Intel HD Graphics 3000.

Could someone tell me, step-by-step, the exact instructions of going about fixing this problem? I'm not too tech-savvy; I only comprehend usage within Windows 7 and know not much about BIOS nor Ubuntu.

---

### Post by oldfred on 2014-05-03
Usually with 14.04 and Intel video it just works.

Some have found that brightness is just set to 0 and you have to use whatever f-key it is to increase brightness.

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by eddy4 on 2014-05-04
Sorry, none of these links actually solve my problem. Here is the full extent of my problem:

- I cannot access my Windows 7 Professional 64-bit OS at all, because I'm stuck at the grub rescue screen
- I cannot boot-up the installed version of Ubuntu (on the external hard drive), and if I go into the HP F9 Boot options menu, and select the USB External Hard Drive for booting, I get a back-lit dark screen, with nothing on it.
- I can only boot using the Ubuntu Live-CD (the "Try it" version of the Ubuntu 14.04 Installation CD that I burned)

Can anyone provide a solution past the "grub rescue" screen so that I can go into Windows 7 and uninstall Ubuntu? Ubuntu has caused me enough problems that I can't necessarily solve, so I would like to remove it as soon as possible. The laptop that is having trouble with this is my main laptop and I would like it back to the state it was in before, and keep all my files that have been made with Windows 7.

---

### Post by LastDino on 2014-05-04
Maybe have a look at this? I haven't tested it though as I don't have windows anymore anywhere, so be careful.
 [http://social.technet.microsoft.com/Forums/en-US/0c328b4d-8427-41cf-be94-5d842ed32fad/windows-7-wont-boot-broken-mbr-help-please?forum=w7itprogeneralhttp://social.technet.microsoft.com/Forums/en-US/0c328b4d-8427-41cf-be94-5d842ed32fad/windows-7-wont-boot-broken-mbr-help-please?forum=w7itprogeneral](http://social.technet.microsoft.com/Forums/en-US/0c328b4d-8427-41cf-be94-5d842ed32fad/windows-7-wont-boot-broken-mbr-help-please?forum=w7itprogeneralhttp://social.technet.microsoft.com/Forums/en-US/0c328b4d-8427-41cf-be94-5d842ed32fad/windows-7-wont-boot-broken-mbr-help-please?forum=w7itprogeneral)

---

### Post by oldfred on 2014-05-04
Did you run Boot-Repair to restore the Windows boot loader to the MBR of the internal drive?
If that is not fixing it or link from Goten0007 does not work post link to BootInfo report from Boot-Repair.
You can install and run Boot-Repair from your Ubuntu live installer.

---

### Post by LastDino on 2014-05-04
That link also tells you to run boot repair with W7 installation DVD. Don't do it with pirated one on genuine machine, use genuine one only which you will have if it is genuine.

If nothing works for you, you can simply use live ubuntu boot and copy all your data to some other drive/take a backup and do fresh install of W7. Again, it is not such a bad choice either.

---

### Post by oldfred on 2014-05-04
Boot-Repair does not run on Windows, only on Linux.
You can download it as a liveCD, or install from the ppa into your Ubuntu installer if you can boot that, or into any working Linux install.

---

### Post by LastDino on 2014-05-04
> **oldfred said:**
> Boot-Repair does not run on Windows, only on Linux.
You can download it as a liveCD, or install from the ppa into your  Ubuntu installer if you can boot that, or into any working Linux  install. 		.

I haven't tested this but looks like something that could work tbh

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Why does it not work when Microsoft support is telling it does? o-o

> 
[h=3]/FixBoot[/h]This option writes a new boot sector to  the system partition by using a boot sector that's compatible with  Windows Vista or Windows 7. Use this option if one of the following  conditions is true:
[LIST]
[*]The boot sector was replaced with a nonstandard Windows Vista or Windows 7 boot sector.
[*]The boot sector is damaged.
[*]An  earlier Windows operating system was installed after Windows Vista or  Windows 7 was installed. In this situation, the computer starts by using  Windows NT Loader (NTLDR) instead of Windows Boot Manager  (Bootmgr.exe).
[/LIST]

---

