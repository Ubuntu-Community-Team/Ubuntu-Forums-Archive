---
title: "Ubuntu partitions deleted, cannot boot bios"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by cloudshift2 on 2014-05-17
Hi guys, this is my walk of shame. 

I had Windows 8 installed and dual booted with Ubuntu 14.04.
I deleted the Ubuntu partitions via Windows, because I needed the space, but didn't repair MBR. I expected to be able to boot Windows from USB and repair from there. 

I cannot boot from USB or a cd, nor access the bios. I press F2, but it always goes into the grub minimum bash-line (version 2.02~beta2-9. If I press F10 during boot, to change the one time boot order, it only says Ubuntu. If I chose it, I'm back to grub minimum bash. 

Is there any way I can make grub boot the windows cd directly or something? Since it's a laptop, I'll lose my warranty if I open it and remove the hdd.. 

Thank you very much in advance!

---

### Post by DhrSchap on 2014-05-17
Grub only kick in after the bootstrap. BIOS will first run the POST (power on self test) If you are quick enough you should be able to access bios, rhytmically-repeatedly press the F2 button while the machine powers up - are you sure f2 is the button to access bios. Are you sure your laptop is of at time of boot (keep power button pressed until it switches of, then try again). You will have to restore the MBR - best bet is probaly the Ubuntu CD.

---

### Post by cloudshift2 on 2014-05-17
I am sure F2 is the key to access bios, as I've used it before.  Also, it says while booting. 

A few minutes ago while I was trying everything, I discovered that F9 makes it boot through the USB (Samsung laptop) . I tried recovering the boot, but to no avail. I have now formatted everything and Windows is installing again. Hopefully everything should be OK. 

It is strange, however, that I couldn't access bios.

Still, thank you!

---

### Post by Luke M on 2014-05-17
This answer comes too late, but for future reference: at the grub prompt, type fwsetup. This will reboot and take you to your BIOS setup.

You were using EFI mode, not legacy BIOS mode, so MBR was not being used. Nothing was wrong with the disk (except that grub no longer had access to grub.cfg - some distros put grub.cfg on the EFI partition so this doesn't happen...)

---

### Post by cloudshift2 on 2014-05-17
> **Luke M said:**
> This answer comes too late, but for future reference: at the grub prompt, type fwsetup. This will reboot and take you to your BIOS setup.

You were using EFI mode, not legacy BIOS mode, so MBR was not being used. Nothing was wrong with the disk (except that grub no longer had access to grub.cfg - some distros put grub.cfg on the EFI partition so this doesn't happen...)

I still appreciate your input.

Actually, I couldn't install Windows 8. Whenever the setup finished and the computer rebooted, a boot window would appear, being the only option "Ubuntu".
However, it wasn't installed, so, nothing booted and the computer turned off.

I reinstalled Ubuntu 14.04 just now, but I really need Windows 8 because of Visual Studio and other tools.
What is the safest way to remove Ubuntu (sorry for asking this here. I'm a big fan of Ubuntu and what it represents, but my laptop's battery is really diminshed and I use my laptop a lot outside), and have a clean Windows 8 install?

Thanks

---

### Post by oldfred on 2014-05-17
UEFI or BIOS?

Windows has to have gpt partitioning if UEFI.
Windows has to have MBR(msdos) partitioning if BIOS.

And how you boot install media is how it installs but if partitioning does not match then it will not work.

With BIOS Windows has to have a primary NTFS partition with the boot flag or unallocated space with available primary partitions. Normal install is two partitions, one 100MB boot and the main install, but it will install to one you that is what you give it.

---

### Post by Luke M on 2014-05-17
You have ubuntu working again? Type
sudo efibootmgr -v

and post the result.

---

### Post by cloudshift2 on 2014-05-17
UEFI.
I'm affraid that if I boot the windows 8 setup and delete/format all the ubuntu partitions and install windows, I'll get the same problem again.
I can't burn CD's and only have a 16gb usb pen. So, I have to format and move the files to it every time I need to switch between the,.

---

### Post by cloudshift2 on 2014-05-17
> **Luke M said:**
> You have ubuntu working again? Type
sudo efibootmgr -v

and post the result.

sudo efibootmgr -v doesn't return anything.
It does run succesfully, but there's no output.

---

### Post by Luke M on 2014-05-17
Just to double check, make sure that /sys/firmware/efi exists (it will exist if you booted in EFI mode, otherwise it won't).

---

### Post by cloudshift2 on 2014-05-17
> **Luke M said:**
> Just to double check, make sure that /sys/firmware/efi exists (it will exist if you booted in EFI mode, otherwise it won't).

That folder does exist. And contains 2 more folders: efivars and vars, plus a file: systab.

---

### Post by Luke M on 2014-05-17
Ok. There's nothing you can do from ubuntu if efibootmgr doesn't work (this also explains why you couldn't install Windows). You have to try fiddling with the BIOS settings:
1. Look for a fast boot option, turn it off.
2. Look for a secure boot option, turn it off.
3. Look for a legacy BIOS (often called "CSM") option, turn it ON.

If you get legacy BIOS mode working, then you can partition your drive as MBR (not GPT), install Windows and/or Ubuntu in BIOS mode and forget about this EFI nightmare. The only case where you need EFI is if you're booting Windows from a >2TB drive.

---

### Post by cloudshift2 on 2014-05-17
> **Luke M said:**
> Ok. There's nothing you can do from ubuntu if efibootmgr doesn't work (this also explains why you couldn't install Windows). You have to try fiddling with the BIOS settings:
1. Look for a fast boot option, turn it off.
2. Look for a secure boot option, turn it off.
3. Look for a legacy BIOS (often called "CSM") option, turn it ON.

If you get legacy BIOS mode working, then you can partition your drive as MBR (not GPT), install Windows and/or Ubuntu in BIOS mode and forget about this EFI nightmare. The only case where you need EFI is if you're booting Windows from a >2TB drive.

Thank you very much for your help, Luke!

When installing Ubuntu it asked me if it was GPT partition or not, stating that it was damaged.

I don't have much time till Tuesday to reinstall Windows. Well, I do, but if I run into problems again, then, not really.
I need a stable laptop for the next few days. I'll use Ubuntu till then, and then follow the steps you mentioned.

Thank you once again for your time!


EDIT: I still can't access the BIOS, when the pc is booting.. How can I get into it?

---

### Post by Luke M on 2014-05-17
> **cloudshift2 said:**
> 
EDIT: I still can't access the BIOS, when the pc is booting.. How can I get into it?

There should be an option in the grub menu (last line).

If not, type "c" at grub menu to get a command line and then type fwsetup.

---

### Post by cloudshift2 on 2014-05-17
> **Luke M said:**
> There should be an option in the grub menu (last line).

If not, type "c" at grub menu to get a command line and then type fwsetup.

Oh right, forgot to mention. It's booting directly into Ubuntu, grub isn't showing up..

---

### Post by Luke M on 2014-05-17
Hold down shift key to make grub menu appear. If that doesn't work, then edit /etc/default/grub file to unhide the menu. Then run sudo update-grub.

---

### Post by oldfred on 2014-05-17
If UEFI it may be the escape key instead of shift key to get grub menu. 
If only one system is installed then it will not normally show grub menu.

If drive is gpt, then you have to boot and install Windows in UEFI boot mode.
       Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

### Post by cloudshift2 on 2014-05-19
I managed to get to the grub menu and the command line by pressing the escape key.
After all, it seems it's still in UEFI mode. Plus, using gparted, the mount point for the boot partition is /boot/efi .

Thing is, fwsetup is not a recognized command in the grub command line.
I still cannot access my bios. Why isn't the bios key (F2) working?

While I'm really enjoying the steadiness and spead of Ubuntu, I really need some applications only available on Windows.

---

### Post by oldfred on 2014-05-19
Did you leave fast boot on. It can be settings in either or both Windows & UEFI. Then you have very little or no time for UEFI key to work as it is a fast boot.
Sometimes a full cold boot will let you into UEFI if quick. Or check you manual for you system.
Turn off system, if laptop remove battery and hold power switch to drain residual power. Wait a bit then reboot.

---

### Post by cloudshift2 on 2014-05-19
Fast boot may be on. I remember that I disabled it, so I could install Ubuntu, but maybe I enabled it again.

Fast boot was never a problem, in that regard, however. The boot screen, that shows the bios key still shows for a few seconds, every time. I've cold booted it many times, while very quickly and repeatedly pressing the bios key, but to no avail. 

I cannot remove the battery, as it's embedded.. 

Is it a viable option to resize my disk, clean the new partition and install windows 8 directly there, and then updating grub? I don't mind keeping Ubuntu, if that's what it takes. Heck, I might even use it as my main OS, and change to Windows only when I need to.

---

### Post by oldfred on 2014-05-19
Other Samsung links. Not sure if any will be helpful or not.

 Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by Luke M on 2014-05-19
> **cloudshift2 said:**
> I managed to get to the grub menu and the command line by pressing the escape key.
After all, it seems it's still in UEFI mode. Plus, using gparted, the mount point for the boot partition is /boot/efi .

Thing is, fwsetup is not a recognized command in the grub command line.


Hmm...what version of grub? I'm using "2.02~beta2", which is what comes with ubuntu 14.04. All I can think of is, you must somehow have an older version installed.

It should be possible to do this from linux, too - but I don't know of any utility to do it (efibootmgr doesn't seem to have such an option). Damn!

---

### Post by Luke M on 2014-05-19
You can boot from USB, right? Boot from ubuntu, you should see grub 2.02~beta2. Hit C, type fwsetup.

---

### Post by cloudshift2 on 2014-05-20
I'm using that version, too. It was a fresh 14.04 install.
Later today I'll repartition the disk and hopefully be able to install Windows.  I'll let you know how it goes. 

Thank you guys

---

### Post by cloudshift2 on 2014-05-30
Just a quick update:

This still hasn't been solved. I've used gparted on a live cd, and then formatted/deleted everything. After that I could booted my laptop, and a pop up still showed up, showing only a 'ubuntu' option. Everything was deleted, so it didn't do anything. 

I installed Windows after, and the same thing happened. I can't access the bios or anything, just boot from USB. 

Installing Ubuntu works, and I've been using it daily. I really like it, but my battery is bad compared to Windows (Nvidia prime is installed and the integrated gpu is chosen, plus tlp tools are installed). 

Ah, as a test, I partitioned the drive for a fresh Ubuntu install, and didn't use the first partition for /boot, it was a blank partition, where i was going to put Windows (for a dual boot). The computer didn't recognize the install, and that nasty, non sense boot loader showed up again. 

After a new automated install, everything was working again. I'm getting acquainted with Ubuntu, but I'm afraid that's the only os I'll be able to run (I'd like to test elementary for example).

Ubuntu installer put my biggest partition (almost 1TB) in the middle of the boot and swap partition. Can I still partition it, and install another OS, or must I delete everything so it stays in the end, and the new OS also stays after the 3 Ubuntu partitions? Thank you!

---

### Post by oldfred on 2014-05-30
Are you in BIOS or UEFI boot mode?

You can always shrink a large partition, but with BIOS you have MBR(msdos) and then a limit of 4 primary partitions. But in the extended partition you can have an unlimited number of partitions, but all logical partitions must be inside the one extended, so you may have to move partitions around.

If you did not totally reformat it may have stayed as gpt as that is what UEFI has to have. But Ubuntu will boot in BIOS mode from gpt.

Post this.
sudo parted -l

I have many installs in my sdc drive each about 25GB and they all share the same data partitions, but not /home.

---

### Post by cloudshift2 on 2014-05-31
It should be in UEFI, I think.

Here's the output for parted -l:

> 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   994GB   993GB   ext4
 3      994GB   1000GB  6213MB  linux-swap(v1)


I also have a 8GB expresscache disk, but it doesn't have any partition (partition table msdos).

---

### Post by Luke M on 2014-05-31
So were you able to enter the BIOS setup using my last suggestion?

---

### Post by cloudshift2 on 2014-05-31
Unfortunately no, it says unknown command for fwsetup..

---

### Post by Luke M on 2014-05-31
> **cloudshift2 said:**
> Unfortunately no, it says unknown command for fwsetup..

And it says "grub 2.02~beta2"?

---

### Post by cloudshift2 on 2014-05-31
Yep, it says '[COLOR=#000000]2.02~beta2-9' . I'm able to access that command line while Ubuntu is booting up, too.[/COLOR]

---

### Post by Luke M on 2014-05-31
Try rEFInd, it has an option to enter BIOS setup:

[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

This might not work if you can only boot in "secure" mode (but give it a try). In that case you would need this version:

[http://en.altlinux.org/Rescue](http://en.altlinux.org/Rescue)

---

### Post by cloudshift2 on 2014-05-31
In case it doesn't work, should I be able to repair GRUB with ubuntu usb?
I think secure boot is active, I must also do this, right? [http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by Luke M on 2014-05-31
> **cloudshift2 said:**
> In case it doesn't work, should I be able to repair GRUB with ubuntu usb?

I think you need to enter BIOS setup to make progress.

> **cloudshift2 said:**
> I think secure boot is active, I must also do this, right? [http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

No. You aren't trying to install rEFInd on your hard drive, you just want to boot it from USB and use it to enter BIOS setup, that's all.

---

### Post by cloudshift2 on 2014-05-31
That just saved me from another headache, thanks.

So, since I wasn't sure SecureBoot was active or not, I went straight to the 'Rescue' distribution.
Turns out that during boot of Rescue, it says that SecureBoot is NOT enabled. That's a good sign, I guess.

I'm not sure what the next step is now, sorry. I tried launching the EFI shell, but it failed.
Knowing that SecureBoot is disabled, I will now put rEFInd in the usb, instead of Rescue.

Thank you for all the help so far, guys.

---

### Post by Luke M on 2014-05-31
> **cloudshift2 said:**
> 
I'm not sure what the next step is now, sorry. I tried launching the EFI shell, but it failed.
Knowing that SecureBoot is disabled, I will now put rEFInd in the usb, instead of Rescue.


In the row of small icons, there should be an "i" for information (please select this - it gives EFI and firmware version information, good to know), as well as icons for shut down, reboot, and reboot to setup (the last one is what you want).

---

### Post by cloudshift2 on 2014-05-31
I don't have reboot to setup, only shutdown and reboot (pressing F2/insert to show more options doesn't do anything).

The boot options are EFI /boot (grub) and 2 Ubuntu images (different kernels).

About returns:
> 
EFI Revision 2.31
Platform: x_86_64 (64 bit); Secure Boot inactive
Firmware: Phoenix Technologies Ltd. 4660.22
Screen Output: Graphics Output (UEFI), 1024x768


---

### Post by Luke M on 2014-05-31
> **cloudshift2 said:**
> I don't have reboot to setup, only shutdown and reboot (pressing F2/insert to show more options doesn't do anything).

The boot options are EFI /boot (grub) and 2 Ubuntu images (different kernels).


Damn, your BIOS is really unfriendly. At least now with rEFInd, you should have the ability to boot into Windows (I assume you don't have it installed at the moment). This should work:
1. Install Windows.
2. Use rEFInd on USB to boot into Windows.
3. For a more permanent solution, copy rEFInd from USB to your hard drive's EFI partition. This will make it the default EFI boot manager.

---

### Post by cloudshift2 on 2014-06-01
Thank you very much! I really need the laptop these days, but I'll reinstall Windows and try that till the end of the week! Again, thank you for your time and help

---

### Post by Luke M on 2014-06-01
> **Luke M said:**
> Damn, your BIOS is really unfriendly. At least now with rEFInd, you should have the ability to boot into Windows (I assume you don't have it installed at the moment). This should work:
1. Install Windows.
2. Use rEFInd on USB to boot into Windows.
3. For a more permanent solution, copy rEFInd from USB to your hard drive's EFI partition. This will make it the default EFI boot manager.

I remembered that Windows installs itself as the default EFI boot manager (efi/boot/bootx64.efi), and yet your BIOS failed to boot it. So step (3) won't work. Instead, you have to copy rEFInd to efi/ubuntu (not efi/boot) and copy or rename rEFInd's bootx64.efi to grubx64.efi and shimx64.efi (either one might be used). Hmm...but this might fail if your system insists on secure boot.

Alternatively, you could use grub like you were originally. We know that works, you just need an appropriate grub.cfg file. The problem you ran into when you deleted the ubuntu partition is that the grub.cfg on the EFI partition is not the real grub.cfg, it just loads the real grub.cfg from /boot/grub/grub.cfg. So if you copy /boot/grub/grub.cfg to /boot/efi/EFI/ubuntu/grub.cfg, then grub will keep working even without the ubuntu partition.

---

### Post by cloudshift2 on 2014-06-20
It didn't work.. Not even other distros.

I ended up sending the laptop to Samsung. They replaced the motherboard and the hard drive.
It seems some computers of the series 3, 5 and 7 are messed up.

Thank you for all your time and help!

---

