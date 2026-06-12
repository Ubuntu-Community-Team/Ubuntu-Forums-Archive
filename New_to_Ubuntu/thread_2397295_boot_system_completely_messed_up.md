---
title: "boot system completely messed up"
date: 2018-07-27
forum: New to Ubuntu
---

### Post by ris-tlp on 2018-07-27
I really wanted to get started with using ubuntu so I downloaded a USB image and installed it. I made sure to install it on a partition which was completely empty and not in use. After doing so, I checked and it was installed in the right place. After changing absolutely nothing, I restarted my pc and it would only boot straight into Ubuntu while I wanted to have the option to boot into Windows as well.
I looked up a few places and was told to sudo update-grub, which I did. Still couldn't get into Windows.
After this, was told to use boot repair to remove grub and restart and I would then boot right into windows. After restarting, I see the GNU Grub command line screen. I changed the boot order in the bios settings and tried restarting, I got "No bootable device insert boot disk and press any key". 
So now I can't open neither windows nor ubuntu.
I acknowledge that I went in blind with absolutely 0 experience and probably messed around with things I have no knowledge about, just want to get it back to normal now.

What should I do?

---

### Post by oldfred on 2018-07-27
No boot drive is usually that you changed UEFI settings from/to UEFI or BIOS/CSM/Legacy.
And then you need to know how both Windows & Ubuntu are installed UEFI or BIOS, so UEFI boot setting can match how you installed.
And how you boot install media, is then how Ubuntu installs UEFI or BIOS. You always want Ubuntu in same boot mode as your Windows install.

Make sure UEFI Secure Boot is off. May be Windows or "other" where Other is setting you want.
Make sure UEFI is on, and CSM/Legacy/BIOS setting is off. My system for some strange reason has UEFI settings under the CSM setting line in UEFI.

You need to get live installer booting.
Some systems also need full cold boot to reset UEFI, not warm reboot. 

Then run this, so we can see details of your configuration and make suggestions on fixes.
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ris-tlp on 2018-07-28
I see. Thank you so much for the detailed answer!
I was able to boot into Ubuntu by initializing the kernel in the grub gnu command line at startup. Here's the bootinfo summary: [http://paste.ubuntu.com/p/YZ9xntW8bX/](http://paste.ubuntu.com/p/YZ9xntW8bX/)
Once again, thank you very much!

---

### Post by oldfred on 2018-07-28
If using gpt for UEFI boot the boot flag must be on the ESP - efi system partition.
But with MBR for BIOS boot, grub does not use boot flag, but you must have boot flag on the Windows boot partition.
Move boot flag from sda6 to sda1. You can use gparted or Windows tools (make active).

You also show the now extremely old grub4dos used by EasyBCD. Usually better to use grub as boot loader in MBR.
But with Windows 10, it will turn hibernation back on with updates and then grub will not boot it. So have Windows repair disk to temporarily reinstall Windows boot loader to fix Windows then use Boot-Repair to restore grub2's boot loader to MBR.

That is where UEFI works better as both Windows & Ubuntu have boot loaders in ESP. And then from UEFI you can choose which to boot at any time. But it is a major change to reinstall Windows in UEFI boot mode.

---

### Post by ris-tlp on 2018-08-01
I see. I had a complete backup of my windows partition before I went so I've completely wiped the disk and changed it to a gpt partition. Doing so has smoothened everything out, installation was smooth. My only issue now is a very slow wifi download speed and overall browsing speed, will ask in the networking section. 

Thanks for the help!

---

