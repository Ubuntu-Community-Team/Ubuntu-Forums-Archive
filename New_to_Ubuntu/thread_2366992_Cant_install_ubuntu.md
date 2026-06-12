---
title: "Cant install ubuntu"
date: 2017-07-24
forum: New to Ubuntu
---

### Post by ncfcdaniel on 2017-07-24
Hi
Just created a USB/disk but I can't install it, I just comes up with a black screen.
This is my pc model: 870-240na
[https://support.hp.com/in-en/product/omen-by-hp-870-200/13687063/document/c05366957/](https://support.hp.com/in-en/product/omen-by-hp-870-200/13687063/document/c05366957/)

---

### Post by oldfred on 2017-07-24
I do not know AMD graphics, you probably need nomodeset. And after install the correct AMD driver, but there are several depending on what version of AMD your card/chip is.

Is Windows UEFI or BIOS? You want to boot Ubuntu installer in same mode as Windows is installed, so Ubuntu is installed it that same boot mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Does your UEFI/BIOS let you turn off AMD and use Intel internal video.And then switch connection to monitor. Some have installed that way then added correct video driver and switched video back.

I think this applies to older HP systems:

 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260) 
      
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
           
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by BenginM on 2017-07-25
Salutations!

Whcih ubuntu version , and kernel base version! When does the black screen displays .. before or after the GRUB bootloader!  lookin' at the machine specs . it appears it has a Hybrid/Dual Video Graphics .. with the Integrated Intel HD Graphics , and an Radeon RX 580R , and according to :

[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx)

I suppose the free driver amdgpu should be loaded by the kernel and detects the RX card , unless the old free driver radeon is in the way ...

[https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
[https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

I'am pretty sure if you disable the discrete Radeon RX 580R , you'll be able to boot with built-in Intel Graphic without a black screen .

try what oldfred suggested . with the live/usb seassion boot with kernel parameter nomodeset ..

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

From the Grub2 menu on boot, highlight the entry you want to boot, press "e" to enter the Edit mode.

Go to the "linux" line and add the "nomodeset" option to the end of the line.

Press CTRL-x to boot.

##

Did you SHA256SUM check the hashes on the iso file before you burn it to the usb. #see:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Also which tool you've used to burn the sio to usb? dd'in the iso to usb never failed me ,, you might want to try that.

Also, you want to consider installing from the mini iso , a netboot installation which requires a wired ethernet .. it's fairly simple .. just make sure when you get to the software selection , highlight the desktop environment package you want , for Unity select ubuntu-dekstop , or if you want lubuntu (lubuntu-desktop .. you select software packages by pressing the space key before you hit continue. 
#see :
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://youtu.be/U42Ln3k7VK0](https://youtu.be/U42Ln3k7VK0)

[https://youtu.be/fIfQ8SehcNU](https://youtu.be/fIfQ8SehcNU)

---

