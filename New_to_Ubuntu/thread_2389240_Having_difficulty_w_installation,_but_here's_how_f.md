---
title: "Having difficulty w installation, but here's how far I got:"
date: 2018-04-13
forum: New to Ubuntu
---

### Post by essex2 on 2018-04-13
I made a working USB w ubuntu on my mac using etch and I can run without installing on my mac, so I think the problem is not in the USB.

I just built a PC, no OS yet, changed the bios settings to boot to disable secure boot (had to clear keys), enable CSM, and boot from USB.
I got up to GNU Grub and have not made much progress after that. When I run without installing, I get error messages mostly and one time I reached the purple Ubuntu loading screen but it didn't go further than that after waiting half an hour. When I chose to simply install, nothing happens as well. 
[IMG]https://imgur.com/i3xtpeQ[/IMG]
[IMG]https://imgur.com/i3xtpeQ[/IMG]

Error screen
[https://imgur.com/3XIiYon](https://imgur.com/3XIiYon)
[https://imgur.com/i3xtpeQ](https://imgur.com/i3xtpeQ)
[https://imgur.com/El06ABM](https://imgur.com/El06ABM)

Bios settings
[https://imgur.com/ZwKnEwq](https://imgur.com/ZwKnEwq)
[https://imgur.com/iSCHMXa](https://imgur.com/iSCHMXa)
[https://imgur.com/uz6ruW2](https://imgur.com/uz6ruW2)

This is the closest I got:
[https://imgur.com/xVKL3KU](https://imgur.com/xVKL3KU)

Any guidance is appreciated, thanks!

---

### Post by oldrocker99 on 2018-04-13
If the PC has UEFI BIOS, and it probably does, just make sure that the USB doesn't boot in UEFI mode, but "legacy." If you don't boot legacy, GRUB will **not** install. Go into the BIOS and boot from the USB in normal mode, and you should be fine. IF you can't boot in normal mode, you'll get a warning on the partition screen, and choose "Go Back." That will set things up in legacy mode, and the installation will be 100% correct.

---

### Post by essex2 on 2018-04-13
> **oldrocker99 said:**
> If the PC has UEFI BIOS, and it probably does, just make sure that the USB doesn't boot in UEFI mode, but "legacy." If you don't boot legacy, GRUB will **not** install. Go into the BIOS and boot from the USB in normal mode, and you should be fine. IF you can't boot in normal mode, you'll get a warning on the partition screen, and choose "Go Back." That will set things up in legacy mode, and the installation will be 100% correct.

Yes, UEFI bios.
Changed all options to legacy
[https://imgur.com/DYnuAvK](https://imgur.com/DYnuAvK)
but still did not get past the GRUB screen :(

---

### Post by oldfred on 2018-04-13
I recommend UEFI, but some still like the now 35 year old BIOS/MBR configuration.
If you really want BIOS boot, but are not installing Windows, you can still use the updated gpt partitioning rather than the old MBR(msdos).
I used gpt with my old BIOS system starting in 2010. When Windows converted to UEFI/gpt, I started adding both the bios_grub for BIOS boot and the ESP - efi system partition for UEFI boot to all new or repartitioned hard drives. Then I could boot either way if I wanted to reinstall grub.

Your setting for "Windows" needs to be "Other". You may find fine print that says you need that change if installing Windows 7 as it does not support UEFI Secure Boot. And I think you need default keys if in UEFI Mode, but that may only be required if UEFI Secure Boot on.

What model motherboard. AMD graphics or something else? If nVidia you may need nomodeset boot parameter.
Some need boot parameters.
       Some Gigabyte boards need acpi=off boot parameter also 
Some need IOMMU settings changes & boot parameters.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by essex2 on 2018-04-13
> **oldfred said:**
> I recommend UEFI, but some still like the now 35 year old BIOS/MBR configuration.
If you really want BIOS boot, but are not installing Windows, you can still use the updated gpt partitioning rather than the old MBR(msdos).
I used gpt with my old BIOS system starting in 2010. When Windows converted to UEFI/gpt, I started adding both the bios_grub for BIOS boot and the ESP - efi system partition for UEFI boot to all new or repartitioned hard drives. Then I could boot either way if I wanted to reinstall grub.

Your setting for "Windows" needs to be "Other". You may find fine print that says you need that change if installing Windows 7 as it does not support UEFI Secure Boot. And I think you need default keys if in UEFI Mode, but that may only be required if UEFI Secure Boot on.

What model motherboard. AMD graphics or something else? If nVidia you may need nomodeset boot parameter.
Some need boot parameters.
       Some Gigabyte boards need acpi=off boot parameter also 
Some need IOMMU settings changes & boot parameters.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

At this point I've tried all combinations of legacy vs UEFI options. UEFI was the only one that actually took me past GRUB to the ubuntu loading screen where it just idled after that.

Motherboard - ASUS ROG B350-F AM4 w ryzen5 2400
GPU - MSI GTX 1050-Ti

---

### Post by oldfred on 2018-04-13
You need boot options. With nVidia it is nomodeset.

 ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu) 
      
 Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[URL="https://ubuntuforums.org/showthread.php?t=2380798"]https://ubuntuforums.org/showthread.php?t=2380798
[/URL]

            [https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1)
To see if your system is impacted (but it basically comes down to being Intel x86 CPUs or temporarily for AMD CPUs) can check for "cpu_insecure" on the bug line in the /proc/cpuinfo output if running the Linux 4.15-rc6 or later.
When testing on AMD Ryzen but with PTI active, indeed, there is a similar performance hit to Intel. But if using a mainline kernel until that patch ends up being there, just reiterating you can boot your kernel with the "nopti" kernel parameter. Intel users can also opt for the nopti switch if they want to retain maximum performance, but it's a potential security risk. The Ryzen impact: 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by essex2 on 2018-04-15
So I tried all manners of setting NOMODESET from grub without any success. Then I figured I'd take the Alexander approach to the gordeon knot. So I removed my GPU and voila, was able to boot and install ubuntu successfully. 

Now I'm stuck w a new problem of trying to install NVIDIA drivers on ubuntu, which from my google searching appears to be another common problem.

---

### Post by essex2 on 2018-04-15
Crap. I was trying this method of installing my drivers [http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux](http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux)

[COLOR=#2F4F4F][FONT=monospace]sudo add-apt-repository ppa:graphics-drivers
[/FONT][/COLOR][COLOR=#2F4F4F][FONT=monospace]sudo apt-get update
[/FONT][/COLOR][COLOR=#2F4F4F][FONT=monospace]sudo apt-get install nvidia-375
[/FONT][/COLOR]Didn't get past the last step, something about process being in use and the terminal got stuck so I killed it, rebooted, and then now I may have bricked everything. I enter my pw in the login and it accepts it but then loops back immediately to the log-in screen :(

---

### Post by oldfred on 2018-04-15
Can you use recovery mode.
Second or third line in grub menu. 

Did you plug the nVidia card back in? Some motherboards have settings in UEFI to use internal video or external video card. So you do not have to open case. Just connect to correct port out.

The -375 is not now the newest driver, but should have worked.
But now you need to totally purge the old driver before attempting to install a new driver.

       # should show newest versions available in addition
ubuntu-drivers devices 
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

---

### Post by essex2 on 2018-04-16
Can't even get back to grub menu after this happens. I had to wipe everything and start over. 
And again, after installing another driver version [390]("http://www.nvidia.com/download/driverResults.aspx/132530/en-us"), then restarting, I again get stuck in a log-in loop.
I followed this [video]("https://www.youtube.com/watch?v=OG4deLa_vK8") to open console log in, then entered mv. Xauthority .xauthority.bak but that didn't even get me out of the log-in loop.
Every time I get to this point, my only recourse is to boot from usb and reinstall :/

---

### Post by oldfred on 2018-04-16
Did you look at comments on the Phoronix link. Back in Feb he could not get it to consistently boot even with newest kernel. But comments may have work arounds or fixes.

Another user with Ryzen.
[https://ubuntuforums.org/showthread.php?t=2389398](https://ubuntuforums.org/showthread.php?t=2389398)

---

