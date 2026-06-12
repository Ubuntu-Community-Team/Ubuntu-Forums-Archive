---
title: "Boot log errors including NVIDIA VGA issue and UEFI and APCI issues"
date: 2018-02-06
forum: New to Ubuntu
---

### Post by richard378 on 2018-02-06
I am duel booting Ubuntu 17.10 on a Gigabyte Z97-HD3 rev 2.1 mothermoard with NVIDIA GTX 970 graphics card.

I have run Linux in virtual machines, but am new to running Linux directly with hardware concerns.

I attached the boot log in a zip file from journalctl -b > bootlog.txt

I am getting an nvidia driver error about the boot needing to be text console and have searched for answers and can't find one that works.  I have added vga=vesafb:off vga=normal to grub but that does not fix it.

Also  I am getting a UEFI boot error in the log 
 06 22:34:10 richard-Z97-HD3 kernel: Couldn't get size: 0x800000000000000e
Feb 06 22:34:10 richard-Z97-HD3 kernel: MODSIGN: Couldn't get UEFI db list

And there are messages requresing a APCI driver and the default APCI driver is not recommended.
I don't know what that means.  How do I get a driver for that? The Gigiabye page says get Linux drivers elsewhere which is unspecific.

Also there are issues with Gnome Screensaver not loading correctly.

There are a few other red issues that seem minor.  I turned off bluetooth as it was causing  errors and I don't have bluetooth on this desktop.  The above four issues are the main ones I don't know how to fix.

---

### Post by oldfred on 2018-02-07
VGA settings are long obsolete.
You need nomodeset boot option until you have install and can then add the nVidia driver using Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL] 
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

If by any chance you install incorrect driver, you must totally purge everything related as new driver will conflict with old driver and old driver settings.

---

### Post by richard378 on 2018-02-07
The boot issue is a problem that seems to be a problem with Fedora in addition to Ubuntu:
[https://bugzilla.redhat.com/show_bug.cgi?id=1497559](https://bugzilla.redhat.com/show_bug.cgi?id=1497559)
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)

I ran the boot-repair disk and the url from the boot repair is:
[https://paste.ubuntu.com/26534440/](https://paste.ubuntu.com/26534440/)

It added a lot of entries to the grub menu but did not change anything regarding the boot error[SIZE=2]
MODSIGN: Couldn't get UEFI db list         [/SIZE]

I reinstalled Ubuntu and am working on the Nvidia driver which from the posts given I reinstalled and booted with nomodeset
I have to install a downgraded driver.  I am trying to do that now.

The info givin suggests I use nvidia-304 as the driver, I installed it, but don't know how to activate it.  Only higher level drivers are visibie in the GUI.  How do I activate nvidia-304 which is recommend for GTX 9xx?

---

### Post by oldfred on 2018-02-07
I think you read chart wrong.
I used to have a nVidia 960gt which used the 304 driver.
But my newer GT 720 uses newer drivers.

The 304 driver is for now very old nVidia cards.

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers

      [/URL]
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX  
    [URL="http://www.geforce.com/drivers"]
[/URL]

---

### Post by richard378 on 2018-02-07
Thank yoiu you are right.  I read the chart wrong.  My system crashed on that driver and I did a full reinstall and it is working now.

I learned several things on Google about my system.

1. I have to sudo apt-get install inel-microcode a known bug that it does not install by default
2. In addition to modset I have to add intel_iommu=on otherwise my USB 3 does not work. [https://ubuntuforums.org/showthread.php?t=2271519](https://ubuntuforums.org/showthread.php?t=2271519)
3. The boot error is found many places on Google as a frequent problem, and there has been no solution to it that I can find.  Somthing to do with secure boot even if secure boot is off it tries to find certificate and has an error.
4. the gnome desktop screensaver is a known bug that suggests reinstalling all packages which seems to be a bit much as I reinstalled the system several times, so I don't believe that will fix it.  It is a known bug on bugzilla also 

I think all that can be fixed for the boot is working.

---

### Post by oldfred on 2018-02-07
I have an Asus Z97 which required or worked better with at least 10 settings in UEFI.
And another desktop with Gigabyte Z170 which only required several UEFI settings. But I have not needed IOMMU, I thought that was for the AMD versions.

Both systems have UEFI Secure boot off, or in Settings it is "Windows" or "Other".

I have gnome-panel/fallback or the old gnome2 like top & bottom panels that seem to work without major issues. 
Also installed 18.04 with gnome-panel.

---

### Post by richard378 on 2018-02-10
You are right about the IOMMU it is not needed.

I determined that the certficates for the UEFI and secure boot were not installed.  I clicked on install default certificates as it fixed the boot problem.
Other OS leaves secure boot enabled with no option to disable it, so I set it on Windows with secure boot disabled option.

I am having a problem with nomodeset not working.  I am getting the following error:
 NVRM: Your system is not currently configured to drive a VGA console
                                        on the primary VGA device. The NVIDIA Linux graphics driver
                                        requires the use of a text-mode VGA console. Use of other console
                                        drivers including, but not limited to, vesafb, may result in
                                        corruption and stability problems, and is not supported.

My /etc/default/grub has the following:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX="acpi=off"

What can I do about the nvidia driver?

---

### Post by oldfred on 2018-02-10
You should not need nomodeset in grub's config file. You only need it on first boot, or until you install nVidia driver.
That may be the conflict you are having.

Normally you want boot parameters on the DEFAULT, but if an issue you need also for recovery mode then you need it on GRUB_CMD_LINUX line.
Recovery mode already has nomodeset.
```
 GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".  


```

New UEFI systems also have settings to turn on/off the internal Intel video. 
Some have had to boot using Intel & plugging monitor into motherboard video port and then installing nVidia driver. Then switch everything back.

You must have correct nVidia driver for your card. If incorrect one installed, you must totally purge as new install will not remove old and you get conflicts.

---

### Post by richard378 on 2018-02-10
The following solved my NVIDIA problem.  It was a BIOS setting.

[https://devtalk.nvidia.com/default/topic/827139/uefi-nvidia-vga-console-complaints-/](https://devtalk.nvidia.com/default/topic/827139/uefi-nvidia-vga-console-complaints-/)
 The message is a little misleading in UEFI mode. What it means it that  the GPU was initialized to a graphical mode using the legacy VGA BIOS,  regardless of whether the system was booted in UEFI mode or not.  Typically this happens if the Compatibility Support Module (CSM) is  enabled in the system BIOS. If you have an option to disable CSM in the  SBIOS, please try that. 				 			
 		 		 		 			 				 										Aaron Plattner
NVIDIA Linux Graphics
 														

 				 				  			 							[#8]("https://devtalk.nvidia.com/default/topic/827139/linux/uefi-nvidia-vga-console-complaints-/post/4514063/#4514063") 			
  				 					Posted 04/22/2015 02:31 PM

---

