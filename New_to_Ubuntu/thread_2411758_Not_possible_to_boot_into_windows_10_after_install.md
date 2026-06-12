---
title: "Not possible to boot into windows 10 after installing ubuntu in dual boot"
date: 2019-02-03
forum: New to Ubuntu
---

### Post by limnoluke on 2019-02-03
Hi everybody,  I installed my first ubuntu every yesterday and so far i really like it. I installed ubuntu on my MSI GP62 with windows 10 already on it and it was ment to be a dual boot installation. During the installation everything went fine. I followed this tutorial ([https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/)) and now I'm happily using ubuntu on my laptop.   I have to admit that when it came to the boot options I did not understand everything a 100%. My machine is using BIOS legacy boot, I think. But I can also select UEFI, but that always brings me back into the boot menu.  However, when I start my laptop I have the option to start ubuntu, two other options about memory and windows 10. But when I want to start with windows 10 it's either giving me a purple screen or a windows message pops us saying  "Recovery  Your PC/device needs to be repaired  Error code: 0x0000225"  I used the usb with the windows 10 boot to reboot windows 10 via usb and i got into the menu but I couldn troubleshoot the problem.  I also installed boot-repair using the command line and ran it three times. So far without success. Those are the URL's that I created so far:  [http://paste.ubuntu.com/p/Gw7xSdJRKP/](http://paste.ubuntu.com/p/Gw7xSdJRKP/) [http://paste.ubuntu.com/p/CqDVGtvSWC/](http://paste.ubuntu.com/p/CqDVGtvSWC/) [http://paste.ubuntu.com/p/G42Xf6cv3n/](http://paste.ubuntu.com/p/G42Xf6cv3n/)  If I run "sudo update-grup" in the command line the output is as follows: Generating grub configuration file ... Found linux image: /boot/vmlinuz-4.15.0-29-generic Found initrd image: /boot/initrd.img-4.15.0-29-generic Found memtest86+ image: /boot/memtest86+.elf Found memtest86+ image: /boot/memtest86+.bin Found Windows 10 on /dev/sda1 done   So my suspicion is that the windows 10 system files and partitions are still there but somehow I can access them when hitting windows in the dual boot. If someone could help me I would really appreciate that.  All the best and have a nice day, Lukas

---

### Post by oldfred on 2019-02-03
Fortunately you have two drives, as Windows 10 in BIOS/Legacy boot mode is not dual boot friendly.
In UEFI boot mode, you can always boot Windows directly from UEFI. And since you have two drives, if you install Windows boot loader to sda, and Ubuntu's grub2 boot loader to sdb and set UEFI/BIOS to boot sdb by default then you can normally dual boot.

But grub only boots working Windows.
And Windows will turn on fast start up which sets hibernation flag and grub will not boot it. Or you may get corruption needing chkdsk which you cannot do from Linux. You then may be able to directly boot Windows from UEFI/BIOS and f8 into repair console to fix it, then change back to booting with grub on sdb.
But still best to have current version repair/recovery (Windows) or live installer(Ubuntu) flash drives so you can make repairs, if needed.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
You may be able to use Boot-Repair to install a Windows type boot loader to sda and grub to sdb. Which it looks like you already have.
If Boot-Repair does not see Windows then you have to use your Windows repair disk or installer with repair/recovery mode to run fixMBR to install Windows boot loader.

With two drives, to not run Boot-Repair's autofix as that always installs grub to every drive. You want to keep Windows on Windows drive and grub on Ubuntu drive.
Shows advanced options in Boot-Repair where you can choose an install and a drive to install boot loader.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

There are advantages of UEFI with gpt partitioning over the now 35 year old BIOS with MBR partitioning. But since already installed probably not worth changing. But if reinstalling Ubuntu consider using gpt partitioning as that can work with both BIOS boot and UEFI boot if correct supporting partitions are on drive. You need bios_grub for BIOS and ESP - efi system partition for UEFI. When I only had BIOS, but UEFI came out, I started using gpt on all new drives, with both partitions, so I could use drive on new system without having to totally backup & repartition.
Windows has to have MBR(msdos) for BIOS boot and gpt for UEFI boot, so very difficult to convert from one type of install to another.

       
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by limnoluke on 2019-02-04
Hi Oldfred,

thanks a lot for your help. 

So if I get this correctly the requirement for being able to dual boot is to "install Windows boot loader to sda, and Ubuntu's grub2 boot loader to  sdb and set UEFI/BIOS to boot sdb by default". I read about setting the default boot to sdb rather than sda, but then I tried and in my boot menu there are such options. I can basically just choose between the different hard-drives (also DVD/CD drive and USB drive) where the BIOS should look for the boot loader (I think). So how do I actually find out where the boot loaders are? 

About your next suggestion: I think I can access the repair console using the windows 10 boot usb that I have. And there I'll write "chkdsk" in to the command promt and hit enter. Is that all that I need to do to fix it? 

Regarding the "fast start up" you are suggesting different methods to turn it off. I'll thry them and see if I succeed with it :)

About the Boot-Repair's tool. I'll then just select the advanced options and choose to install the windows on sda and grub und sdb, right? Can it be that for this step it might be important if the partitions that I created during the Ubuntu installation (sdb) are "primary" or "logical"?

I'll try all these approaches out as soon as I have time. I actually just want to have this dual boot option for a couple of months or so to get into using Linux. The long term goal is to completely delet windows from my machine. And when I do that it'd probaply also make sense to try UEFI instaed of BIOS. I have one last question: UEFI and legacy... I have all of those options in my boot menu (which is BIOS, I read somewhere). The only one allowing me to actually boot an OS is legacy. But if UEFI is a completely different thing than BIOS, how should that ever be possible to work if I selcet that from within the BIOS boot menu?

Thanks a lot again and I really appreciate your help. Have a nice day,
Lukas

---

### Post by oldfred on 2019-02-04
What brand/model system?
Many have settings for Secure boot that say "Windows" or "Other", but say to use "Other" for installing Windows 7 as it does not support UEFI Secure Boot.
Have you updated UEFI for your model? Most need that.

The three links for fast start up, I think are the same. But Windows has some different ways to change it.

It took me 4 years to stop dual booting XP. I had one application that would not run in Ubuntu and the equivalents were not as good. But after several years the hassle of booting Windows and rebooting Windows for update and rebooting Windows for updates add infinitium, each time I booted into it (once per week) was too much. 

You only may need chkdsk if Windows has corruption. But the fast start up may get turned on with Windows updates that you may not see. So only if grub does not boot it, will you need to go into UEFI/BIOS and boot sda/Windows drive directly.

Boot-Repair report shows which boot loader is installed in each MBR. MBR is only used by BIOS boot. UEFI uses an ESP - efi system partition with gpt partitioning.

---

