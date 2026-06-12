---
title: "Grub Bootloader not working (Dual Boot with Windows 8.1)"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by gio2 on 2014-09-13
Good day, everyone!

I've decided installing Ubuntu 14.04.1. After installing, my laptop booted to Windows 8.1.

I've tried using Boot-repair following these instructions:

> **2nd option : install Boot-Repair in Ubuntu**

 - either from an Ubuntu live-session ([boot your computer on a Ubuntu live-CD or live-USB]("https://help.ubuntu.com/community/BootFromCD") then choose "Try Ubuntu") or from your installed Ubuntu session (if you can access it) 
- connect to the Internet 
- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type the following commands (press Enter after each line): 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)

However, it said that there were errors encountered. I don't know what to do next.
Here's the Boot Info summary. Hope somebody can help me here. [CLICK HERE]("http://paste2.org/5b3LB5CL")

---

### Post by oldfred on 2014-09-13
Install looks normal and Boot-Repair flags the slightest error as final error.
Many systems would just work as you have configured it.

It says it reinstalled grub correctly as error 0 is no error code.
 Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

But I see mention of Sony and dual video, both of which are issues.
Sony's only boot Windows and work arounds are required.
And dual video has issues until correct drivers are installed but getting there can require some effort.
Can you set which video you boot with either Intel or nVidia? Or does it auto switch. We need to know which video mode you boot with that the boot parameters are different. Not sure if now you just want the latest nVidia or need bumblebee to manage dual video.

What model Sony?
Sony users have posted at least two different work arounds that work. 
One is copy grub/shim files into the /efi/Boot folder ( see line 23 in your linked report) and rename grub to bootx64.efi. Then boot hard drive entry from UEFI menu. 
Others use efibootmgr and change name. But not sure if then you can directly boot Windows, or only can boot from grub menu. I prefer to keep directly booting from UEFI menu if possible. Also now Windows 8.1 seems to always want to reset itself as first in UEFI boot order.

      
  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)

 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

 Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
      
 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

           
 Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

---

