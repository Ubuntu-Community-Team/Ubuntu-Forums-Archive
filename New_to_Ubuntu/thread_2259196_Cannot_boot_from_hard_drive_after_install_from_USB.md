---
title: "Cannot boot from hard drive after install from USB"
date: 2015-01-02
forum: New to Ubuntu
---

### Post by Ben_Wyser on 2015-01-02
Hello,

I created a bootable USB stick to install Ubuntu onto a new Toshiba (Satellite C55D-B) notebook.  The installation seemed to go fine.  However, now I cannot get the laptop to boot from the hard drive.  I receive the message "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key".

I have poked around and can see that this issue comes up from time to time, but I can't quite tell which of the various solutions might apply in my case.  I was hoping that someone more experienced might be able to help pinpoint the problem using my Boot-Repair output?

[COLOR=#000000][FONT=-apple-system-font]http://paste.ubuntu.com/9662371/

I'd appreciate any help that anyone can offer.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-01-02
Welcome. Might be a silly question, but have you taken out the USB installer, rebooted, and made sure the machine is booting from the hard drive now and not set to boot from the USB? Check the BIOS if you have set that. 

Did you run the recommended repair option in Boot Repair and no go?

---

### Post by Ben_Wyser on 2015-01-02
I've gone into the BIOS and verified that the boot sequence is set to HDD then USB.  So this is not the issue, I don't think.

And yes, I did recommended repair option in Boot-Repair and am still encountering the same issue.

---

### Post by grahammechanical on 2015-01-02
It seems that you have a UEFI boot system. although people still say BIOS. Is the machine booting in EFI mode and Ubuntu installed in Legacy (BIOS) mode? Or is Ubuntu installed in EFI mode but the machine is booting in legacy mode.

Boot Repair detected that a bootloader was not installed in the MBR of sda (the hard disk). Boot Repair rectified that and installed the appropriate boots files for an EFI boot. So, make sure that you have not switched things to Legacy boot and that you have 

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Oh, by the way, when it comes to experience in UEFI boot systems, you now have more experience than me. A lot of us here do not have the latest hardware. Even Ubuntu developers do not have the latest hardware.

Regards.

---

### Post by bob_t2 on 2015-01-03
I had my boot record originally set to legacy and had to switch to UEFI to boot from USB.  After I build uBuntu on my hard drive, I had to set it to lagacy and set my hard drive first.

---

### Post by oldfred on 2015-01-03
It seems Toshiba is one now that has embedded in its UEFI a requirement to only boot the Windows efi entry. There are several workarounds, some better than others depending on your configuration or hardware.

Since you just have Ubuntu, rename the ubunty entry to read Windows and it should boot the "Windows" entry into grub, shim is the secure boot version of grub that will boot either way. you can use grubx64.efi instead, if not secure boot.
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v

        sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You can run efibootmgr again to see if entry is there.

Info on efibootmgr

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Other workarounds, creating /EFI/boot and copy grub & shim into that folder. Then rename one or the other to bootx64.efi. Then boot hard drive entry which does not have the description check.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

      
 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by Ben_Wyser on 2015-01-13
oldfred,

Thanks for the post.  I am still having problems, unfortunately.  I tried your first recommendation, and it hasn't worked.  First, I could not run efibootmgr without first downloading it using the command

sudo apt-get install efibootmgr

So I first ran that command, then executed the commands you told me.  After...

sudo efibootmgr -v

...the output was as follows:

BootCurrent: 000A
Timeout: 0 seconds
BootOrder: 0000,0001,0002,0008,0009,000A
Boot0000* ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0008* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0009* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot000A* UEFI:  USB DISK 3.0 PMAP    ACPI(a0341d0,0)PCI(12,0)USB(1,0)USB(1,0)HD(1,1f80,1ce4080,29130695)..BO

I then ran...

sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

...and the output was...

BootCurrent: 000A
Timeout: 0 seconds
BootOrder: 0003,0000,0001,0002,0008,0009,000A
Boot0000* ubuntu
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller
Boot0008* UEFI: IP4 Realtek PCIe FE Family Controller
Boot0009* UEFI: IP6 Realtek PCIe FE Family Controller
Boot000A* UEFI:  USB DISK 3.0 PMAP
Boot0003* Windows Boot Manager

Finally, I ran...

sudo efibootmgr -v

...again, and the output was...

BootCurrent: 000A
Timeout: 0 seconds
BootOrder: 0003,0000,0001,0002,0008,0009,000A
Boot0000* ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* Windows Boot Manager    HD(1,800,100000,f1993d5d-410d-45fc-8be1-09de8506c990)File(\EFI\ubuntu\shimx64.efi)
Boot0008* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0009* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot000A* UEFI:  USB DISK 3.0 PMAP    ACPI(a0341d0,0)PCI(12,0)USB(1,0)USB(1,0)HD(1,1f80,1ce4080,29130695)..BO

I then attempted a reboot without the USB stick and still got the same error, that I should insert a bootable medium.

Does it look like I did this correctly?  If not, please let me know where I went wrong.  If so, it doesn't seem to have worked, but I am a bit confused by the other possible fixes you list.  (I will elaborate on my confusion if it doesn't look like I've made some silly error here.)

Ben

---

### Post by oldfred on 2015-01-13
Post this from live installer booted in UEFI mode:
sudo efibootmgr -v

If Windows entry is not working we can do the workaround for those with Windows where we create a hard drive boot entry. 
       From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
mount /dev/sda1 /mnt
#only if not already existing, 
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# make grub be hard drive boot entry in UEFI. 
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

Not sure if after a reboot for two UEFI auto registers the hard drive entry, or if we have to create it.

---

### Post by oldfred on 2015-01-13
From UEFI boot menu or one time boot key can you choose the Windows boot entry? 
And in UEFI boot menu make Windows first and everything else lower in boot priority?

---

### Post by Ben_Wyser on 2015-01-13
Sorry, I am not sure how to get the live installer to boot in UEFI mode.  I guess this isn't happening since efibootmgr isn't available to me by default.  But I'm not sure how to change this.

As for the second possibility, I tried your first command ("mount ...") from a terminal window and it responds "only root can do that".

---

### Post by sudodus on 2015-01-13
1. If the computer UEFI/BIOS system is set in UEFI mode, DVDs and USB pendrives made with Ubuntu desktop 64-bit iso files will boot automatically in UEFI mode.

2. Run as root with sudo

```
sudo mount /dev/sda1 /mnt
```

---

### Post by Ben_Wyser on 2015-01-13
By "UEFI boot menu" are you referring to if I go into startup (i.e. "the BIOS" although I realize it is no longer called this) as the computer is starting up?

If so, I don't see any option for this.  All I can see to do is change the boot priority but my choices are only HDD versus USB, etc.  Nothing specifically referring to the Windows boot entry.

It seems that whatever I did with efibootmgr (as described in the prior post) is not persisting from one boot to the next.  After rebooting I ran "sudo efibootmgr -v" again (only after having to install efibootmgr, I do understand that if I boot the live installer in EFI mode, this should be available to me by default, but as mentioned in the previous post, I am not sure how to accomplish this), I get the following, which contains no mention at all of the Windows thing:

BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0000,0001,0002,0003
Boot0000* ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(2,3)PCI(0,0)MAC(f8a963eeae9b,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* UEFI:  USB DISK 3.0 PMAP    ACPI(a0341d0,0)PCI(12,0)USB(1,0)USB(1,0)HD(1,1f80,1ce4080,29130695)..BO

---

### Post by Ben_Wyser on 2015-01-13
OK, if (1) is the case, then I should be booting automatically in UEFI mode, because I have verified in my UEFI settings that the computer is booting in UEFI mode.  Yet I do not have efibootmgr available by default.

Thanks for clarifying on point (2)...there's a reason I am posting in the newbz forum.  I will try again.

---

### Post by Ben_Wyser on 2015-01-13
OK, sorry for all of the silly questions, but oldfred's second suggestion seems to have fixed my problem, after the clarification from sudodus.  I can now finally boot into Ubuntu without use of the USB stick.

Thanks so much for your help.

---

### Post by oldfred on 2015-01-13
Glad you have it working. :)

If other issues not related to booting pop up start a new thread.

Bit surprised that Windows entry did not work. 
Did bootx64.efi or hard drive entry auto appear in UEFI menu?

When booting live installer UEFI should have two choices, one clearly UEFI - name of flash drive and the other is just the name of the flash drive and will be a BIOS boot.

---

