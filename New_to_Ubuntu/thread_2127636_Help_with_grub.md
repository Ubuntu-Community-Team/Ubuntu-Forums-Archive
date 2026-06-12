---
title: "Help with grub"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by var27rag on 2013-03-20
Hi,

I am new to Ubuntu and i messed up the installation a bit.
I am running Windows 7 and wanted to install ubuntu alongside. I've done this before with older versions successfully but this time i forgot an important step.
While installing the Ubuntu 12.10, I forgot to create the boot partition and then my system refused to boot to my hard disk.
I booted to a live usb and tried to perform a boot repair by using the tool provided, I created a boot drive using gparted and when the boot repair installed grub in the boot partition but was not able to remove grub from the original boot. when i booted next time, i boot to the grub command line. From here i am able to boot to Win 7 but I am not able to boot to ubuntu. The command "kernel /vmlinuz root=/dev/hda3" works, but when i give the command "boot" it gives a lot of lines of something I can't catch but stops after a while saying something about usb found and gives a serial number.

I request your help on trying to boot to ubuntu. I would like to avoid formatting my entire hd as this is the easy way out and I wouldn't learn anything.

Thank You in advance for all the help.

var27rag

P.S.: I am currently working on windows, i am able to boot to ubuntu only with live usb .

---

### Post by oldfred on 2013-03-20
I think we need details. From live USB install Boot-Repair and post link.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by var27rag on 2013-03-20
Thanks for the quick response.
Here is the link with bootinfo
[http://paste.ubuntu.com/5632330/](http://paste.ubuntu.com/5632330/)

Should I try a boot repair again

---

### Post by oldfred on 2013-03-20
You still have grub legacy in the MBR. 

Boot-Repair should fix it, but has to do a full uninstall of grub legacy & grub2 and reinstall of grub2 to make sure everything is correct. Try that first. If not post new BootInfo report.

---

### Post by var27rag on 2013-03-21
I used Boot-Repair, grub2 in now installed in my system and I am able to boot smoothly to both WIn7 and Ubuntu.
Thank you very much for your help.

---

### Post by var27rag on 2013-03-21
I noticed some changes took place in the boot-repair info. I found this in the first info generated:

> [COLOR=#666666]=[/COLOR][COLOR=#000000]> Grub Legacy [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]v0.97[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] is installed in the MBR of /dev/sda and looks on the [/COLOR]
    same drive in partition [COLOR=#008800]*#5 for /boot/grub/stage2 and /boot/grub/menu.lst. *[/COLOR][COLOR=#000000] [/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]> Syslinux MBR [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]4.04 and higher[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] is installed in the MBR of /dev/sdb.[/COLOR]

Could you please tell me what this meant?

---

### Post by oldfred on 2013-03-21
Syslinux is a Windows type boot loader that just looks for the partition with a boot flag and jumps to that partition's PBR or partition boot sector to find more boot code.

Grub legacy & grub2 do not use boot flag but have additional boot code on the drive, usually just after the MBR and that code then searchs and finds the grub menu in the partition that you boot from. 

General info on how BIOS and MBR(msdos) systems have booted since the beginning of hard drives with PCs. Refers to Vista but still the same. New computers with Windows 8 now use a new system UEFI with gpt partitioning.

       Multibooters, Pictures here worth 1000+ words (or long article if interested, but graphics explain it well).
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

