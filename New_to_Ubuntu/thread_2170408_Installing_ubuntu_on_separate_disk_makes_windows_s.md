---
title: "Installing ubuntu on separate disk makes windows stop booting"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by Austin_Seagers on 2013-08-26
Hi All,

I'm fully aware that I must be doing something wrong when installing, but I have ruined a perfectly good windows install so-far and would like some advice to check I'm doing the right thing ;)

My set-up is a home-built desktop build with multiple hard drives. I have a windows dedicated drive and would like to install Ubuntu 12.04 to another completely separate physical disk.

So far, I have wiped both install disks intended for win7 and ubuntu, installed win7 to the first drive, and booted into that numerous times. No problems... Next, I installed ubuntu whilst having disconnected all drives except the HDD I was installing ubuntu onto. Again, that install process went fine. I've restarted and booted back into that drive with no problems (still with only 1 drive connected to my PC)

Now, when I try to put both together and connect all my d[FONT=verdana]rives and boot, manually choosing the windows boot disk in BIOS[/FONT] giv[FONT=verdana]es me "[COLOR=#000000]DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". But ubuntu will still boot, unaffected.

[/COLOR][COLOR=#000000]I'm really struggling to understand what's going on, as the windows disk was not connected to the PC when I installed ubuntu.[/COLOR]
[COLOR=#000000]Can someone please tell me where I'm going wrong?

Many thanks,
Austin[/COLOR][/FONT]

---

### Post by zero2xiii on 2013-08-26
Hay,

This might not be the best approaches. Keep the windows drive connected so it gets added into grub. I would think windows might be installing th MBR to the wrong (First?) drive. Or that your BIOS does not like having numerous boot records.

Keep the windows drive connected and just re-install grub (you can find a link to grub in my signature, or the help us help you have a link to boot repair.).

You can also try and re-install the MBR from a windows CD, not sure on how to do it on a win 7 CD though, never had to myself. Last thing you can try is making sure you install all drives one by one. Disconnect everything except the windows drive, install, and repeat for linux. Although I think you will have the exact same issue.

Cheers

---

### Post by verymadpip on 2013-08-26
Hi there.
Have you tried setting your Ubuntu drive to boot first in the BIOS?  Just to see what happens?
I'm also booting W7 from its own HDD.
Personally, I install grub to my Ubuntu HDD, set that as the first HDD to boot & I usually have no problems.
I suppose it all depends on where grub is living.

---

### Post by eternal243 on 2013-08-26
Well, if you can get Ubuntu to boot, but not windows, then it is probably just a problem with your GRUB configuration. I'm not that good with GRUB, but it seems to me that you either don't have a Windows entry within GRUB or that the Windows entry in GRUB is looking at the wrong partition/harddrive when trying to boot Windows.

---

### Post by Quackers on 2013-08-26
Grub should be installed on his Ubuntu drive only so if choosing the Windows drive in BIOS it shouldn't be affected. Windows should boot normally as it should be untouched by the Ubuntu installation if it was disconnected at that time.
Austin_seagers, out of interest did you re-connect all drives in the same way that they originally were - same drive in the same plug?

---

### Post by Mark Phelps on 2013-08-26
You need to have the following:
1) GRUB  installed to the Ubuntu drive, NOT to the Windows drive
2) Windows drive disconnected when you install, or reinstall GRUB
3) Booting from the Ubuntu drive, not the Windows drive

Having the Windows drive connected resulted in GRUB being installed to THAT drive, not to the Ubuntu drive.  Furthermore, depending on how Win7 boots, that can hose up the Windows booting in the process.

Since you have Windows installation media, do the following:
1) Disconnect the Ubuntu drive
2) Boot from your Windows DVD and choose Repair Install.  Do that three times.  Confirm that Windows boot from that drive.
3) Disconnect the Windows drive, connect the Ubuntu drive, boot from your installation media
4) Install GRUB to the Ubuntu drive -- see: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
5) Reboot, confirming that Ubuntu now boots OK
6) Shutdown, reconnect the Windows drive -- but continue to boot from the Ubuntu drive
7) Boot into Ubuntu, once there, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config file and you should see it detect the Windows 87 Loader.
8) When you reboot now, you should get a GRUB menu with entries for Ubuntu and Windows 7.

---

### Post by Quackers on 2013-08-26
He didn't have the Windows drive connected when he installed Ubuntu.

---

### Post by oldfred on 2013-08-26
May be best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Austin_Seagers on 2013-08-26
Hi all,

Thanks for all your suggestions. As both Ubuntu and Win7 installs are fresh, I decided to just re-install Win7 with no other drives connected and save a headache of attempting to fix the MBR of my Win7 drive.

Still, quite weird that the ubuntu install managed to stop another drive from booting. I don't want GRUB to handle which OS I load, I want them to be completely separate (mainly out of experience with using the BIOS device selection to decide which OS I want to boot)

---

### Post by oldfred on 2013-08-26
If you installed Windows with other drives connected and one of the other drives was the Boot drive in BIOS, Windows would have put its Boot partition on that drive not the drive you installed Windows into. So it may  have been a Windows install issue?

---

