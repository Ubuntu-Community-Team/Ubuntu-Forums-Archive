---
title: "dual boot Windows10 Ubuntu : not detecting existing SSD at Ubuntu install stage"
date: 2018-12-20
forum: New to Ubuntu
---

### Post by 71flax on 2018-12-20
Hi everyone,


  I want to dual boot (Windows 10 v1803/Ubuntu 18.04 LTS) my Dell XPS15. I am inexperienced so I’ve followed this tutorial:
  [https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557](https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557)



  To summarize I’ve taken these steps:
  [FONT=Calibri]-        - [/FONT]Fast Startup disabled

  [FONT=Calibri]-       -  [/FONT]Secure Boot disabled which led to Windows 10 to ask for BitLocker keys on following restart

  [FONT=Calibri]-        - [/FONT]Create a 200 GB partition on my 512 GB SSD

  [FONT=Calibri]-       -  [/FONT]Flashed Ubuntu ISO off Ubuntu’s website onto a 32 GB USB stick with etcher.io

  
[ATTACH=CONFIG]281971[/ATTACH][ATTACH=CONFIG]281972[/ATTACH][ATTACH=CONFIG]281973[/ATTACH]

I manage to boot off the USB into Ubuntu Live but when I proceed to install Ubuntu onto the partition it only offers the USB stick as a device to install to. In other words my SSD doesn’t show up at all when in Ubuntu Live: no SSD and no partition whatsoever…

  I suspect BitLocker to be an issue but I’m clueless at this stage, any help appreciated! Thanks

---

### Post by oldfred on 2018-12-20
Do not know bitlocker issues.
Have you updated UEFI from Dell and firmware for SSD? Most Dell need those updates.
Have you changed drive from RAID or Intel SRT to AHCI?
What video do you have?

Dell issues are common across many similar models.
       Ubuntu 16 on the DELL XPS15 9550 Tutorial
[URL="https://ubuntuforums.org/showthread.php?t=2345444"]https://ubuntuforums.org/showthread.php?t=2345444
[/URL]
 Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en) 
      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560) 
    [URL="https://ubuntuforums.org/showthread.php?t=2345444"]
[/URL]

---

### Post by 71flax on 2018-12-20
Thanks a lot for swift answer, I'll get to it and let you know.

---

### Post by 71flax on 2018-12-21
My setup dell XPS15 9570, graphics card NVIDIA GeForce GTX 1050 Ti, Toshiba 512GB SSD KXG50ZNV512G NVMe

So far I've:

- updated BIOS to 1.6.0
- updated SSD driver from [https://ssd.toshiba-memory.com/en-emea/download/](https://ssd.toshiba-memory.com/en-emea/download/)
- changed drive from RAID to AHCI

However  upon restarting Windows 10 gets stuck on the blue screen below. I've  set drive back to RAID and am writing this message now for further  assistance please. Any ideas?

Thanks

---

### Post by oldfred on 2018-12-21
In Windows you also need to update driver to AHCI.
I think one of the Dell links discusses Windows driver vs. a driver by the NVMe drive vendor in Windows.

If nVidia, you also will need nomodeset boot parameter. Both boot of live installer and initial boot of installed system or until you install nVidia driver from Ubuntu or ppa.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
       Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
    
       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by 71flax on 2018-12-23
Thanks OldFred, it's all sorted now!

Changing RAID to AHCI following this got me going:

 [FONT=&quot]Switching from RAID to AHCI is significantly simpler than switching from AHCI to RAID. All that's needed is a successful boot to Safe Mode.[/FONT]
  
[LIST=1]
[*][FONT=&quot]To set the default boot mode to Safe Mode, use      [/FONT][FONT=&quot]msconfig.exe[/FONT][FONT=&quot] or      open an admin cmd/PowerShell window and run:[/FONT]
[/LIST]
  [FONT=&quot]bcdedit /set '{current}' safeboot minimal[/FONT]
  
[LIST=1]
[*][FONT=&quot]Reboot and hit F2 to enter the BIOS.[/FONT]
[*][FONT=&quot]Change the SATA mode to AHCI.[/FONT]
[*][FONT=&quot]Save and reboot.[/FONT]
[*][FONT=&quot]After Windows successfully boots into Safe      Mode, disable Safe Mode with [/FONT][FONT=&quot]msconfig.exe[/FONT][FONT=&quot] or open an admin cmd/PowerShell window and      run:[/FONT]
[/LIST]
  [FONT=&quot]bcdedit /deletevalue '{current}' safeboot[/FONT]
  
[LIST=1]
[*][FONT=&quot]Reboot one last time. If you open the Device      Manager, there should now be a [/FONT][FONT=&quot]Standard NVM Express      Controller[/FONT][FONT=&quot] device under Storage      Controllers.[/FONT]
[/LIST]
  
On to learning bash & python now, I'm a happy bunny! I'd have taken way longer fixing this dual boot without your help, thanks again

---

