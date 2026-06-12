---
title: "Reboot and select proper boot device or insert boot media in selected"
date: 2014-11-04
forum: New to Ubuntu
---

### Post by Monkop on 2014-11-04
I've installed Ubuntu 14.04.1 onto a new Win8 laptop, overwriting windows. However when I reboot after installation it gives the error:

"Reboot and select proper boot device or insert boot media in selected Boot device and press a key"

I've selected the hard disk to boot from, and I've run Boot-Repair from an ubuntu live session but this error persists.

[http://paste.ubuntu.com/8823858/](http://paste.ubuntu.com/8823858/) is my log.

Any help?

---

### Post by laika2 on 2014-11-25
Dear all,
 I have exactly the same problem.

I have a clean mint install of Ubuntu 14.04.1 on a brand new harddisk. It keeps telling me
"Reboot and select proper boot device or insert boot media in selected Boot device and press a key"
regardless of what I try.

No, it's not some hardware problem. The Ubuntu live CD boots and runs perfectly.
No, it's not the harddisk: I took another one that works for sure, formatted it, installed Ubuntu on it from scratch, and the results are just the same.

I ran Boot-Repair from ubuntu live session twice: the first time I ask boot-repair to repait Grub, and the second time I ask it to restore the master boot record.
Here is my log: [http://paste.ubuntu.com/9228315](http://paste.ubuntu.com/9228315)

The system used UEFI instead of BIOS, and a google search shows that I'm not the only with this problem, but I cannot find a solution.
Also on this forum there are multiple treads with the same boot problem, either with a fresh clean Ubuntu-only installation, or with dual-OS.

Can anybode shed a light on the nature of the problem and or provide us with a solution?
Thanks,

Laika,
still orbiting...

---

### Post by yancek on 2014-11-25
At the top of the boot repair script you will see " Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda".  You should have Grub2 installed to the master boot record which is the default option during the install if you want to install in MBR mode which you have done.  Your computer may be UEFI capable but you have not installed it with UEFI as it would have a separate FAT32 partition which you do not have.  This partition contains the Ubuntu efi files to boot Grub/Ubuntu.  You just have the Linux/Ubuntu system partition (sda1) and the swap (sda5).  You could try reinstalling Grub to the mbr from the installation medium:  sudo grub-install /dev/sda.

You may need to change a BIOS setting so it is not booting EFI.

---

### Post by oldfred on 2014-11-25
@laika
Yancek has diagnosed your issue. You overrode the suggested repair by Boot-Repair to install grub2's boot loader to MBR, so it just installed the generic Windows type boot loader syslinux. 

@Monkop
Did you resolve your issue? Do not know how I missed it?
Yours is a UEFI boot, and many brands, models of systems have internally modified UEFI to only boot the UEFI entry with Windows in the description. There are several work arounds. But since you only have Ubuntu it may be easier just to change the UEFI entry from ubuntu to Windows.        [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
    See D:

 
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

You can use shimx64.efi if you want secure boot or just use grubx64.efi entry if you do not use secure boot.
Your UEFI should have two entries, both in UEFI may say ubuntu. The only difference is one is shim and the other grub.

       modprobe efivars
sudo efibootmgr -v

---

### Post by laika2 on 2014-11-26
Dear all,

I'm up and running again! Thanks.

I went through some frustrating tests and fiddlings with the boot-repair tool. I went through websearch-sessions around partition tables, MBRs, GPT partition map, etc. I even performed my very first firmware upgrade ever, but all without much luck.

The 
[COLOR=Navy]For info on UEFI boot install & repair:
[/COLOR] [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
gave me the winning clue: "boot the DVD in UEFI mode" it says. I know what is meant with UEFI, and EFI and BIOS, but on a brand new UEFI motherbord everything is UEFI-mode, you would think. Wrong! Aha, there is such thing as a UEFI mode, and that crucial thing is pretty poorly documented....

I managed to boot indeed in UEFI mode; I went from scratch through the entire installation again, and all of a sudden, without other manipulations, tweaks, and boot-repair sessions, I found myself with a working and smooth-booting Ubuntu system!

Thanks for the help guys. 

cheers,
Laika,
still (again) orbiting

---

