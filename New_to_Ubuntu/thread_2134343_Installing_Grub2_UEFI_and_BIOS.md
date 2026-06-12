---
title: "Installing Grub2 UEFI and BIOS"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by Aiken Pandora on 2013-04-10
hey,
is there any way to install a BIOS Grub2 Bootloader next to an existing UEFI Grub2 Bootloader? If possible on the same partition.
Didn´t found anything for that topic, but i have to admit, i didn´t knew what i should searching for.

And one extra question, why is my /boot/efi partition empty and the grub2 is installed in my root partition? Is this normal?

---

### Post by oldfred on 2013-04-11
Ubuntu (and Windows) install in either UEFI or BIOS based on how you boot install media.

So if you boot flash drive in BIOS mode it will install in BIOS mode.

Windows will only boot from gpt partitioned drive with UEFI, and only use UEFI if drive is gpt.
Ubuntu will boot in BIOS mode from either MBR(msdos) or gpt partitioned drives.

Boot-Repair will convert a BIOS install on gpt drive to UEFI install if you have efi partition. Or convert from UEFI to BIOS if you want. It unstalls grub-pc(BIOS) and installs grub-efi(UEFI). If secure boot systems there also are versions that are signed. But you have to boot in UEFI mode to change to signed mode of UEFI.

Best to post link to BootInfo Report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Aiken Pandora on 2013-04-11
so there is no way to have Grub2 installed for BIOS and UEFI at the same time?
Like on the Live-CD were Grub2 and Syslinux is bundeled?

and why cant i chose any partition on my flash drive for a separated UEFI Partition?

---

### Post by Aiken Pandora on 2013-04-11
got it recognizing my efi partition, was a bit tricky, had to copy the files from my Windows EFI in there. Dont know why.

[http://paste.ubuntu.com/5698500/](http://paste.ubuntu.com/5698500/)

---

### Post by Aiken Pandora on 2013-04-11
so now i got a new plan, to just install a Bios Grub2 Loader, the problem is, it wont start, i tried some configurations but its all the same, when i try to boot the Drive, the PC just restarts.
Got 2 BOOT-Repair files, the second one is the one which is now in place.
[http://paste.ubuntu.com/5700403/](http://paste.ubuntu.com/5700403/)

[http://paste.ubuntu.com/5700418/](http://paste.ubuntu.com/5700418/)

someone got any idea what i do wrong?
When i use it to Configure a UEFI-Boot, everything works just fine, but i don´t get BIOS-Grub up and running.
Tried everything, i even put the bios-boot Partition at the start of the Drive, didn´t helped.

---

### Post by oldfred on 2013-04-11
If you boot in BIOS mode from a liveDVD or flash drive you should get an install in BIOS mode. With multiple drives you do want to specify which drive's MBR to install grub2 boot loader into.

But you cannot dual boot BIOS and UEFI without full cold boot and going into UEFI/BIOS and resetting from one or the other. UEFI writes data used by operating system differently than BIOS. You could dual boot that way but it is a real hassle.

You have to boot live installer in BIOS mode.

Your install in sde shows in fstab several different entries for /boot. I suggest you do not have a separate /boot. Neither efi for UEFI boot or bios_grub for BIOS boot are used for system boot files. They just have grub startup boot files. The rest of grub and the kernels are in the /boot folder in your install and generally does not need to be a separate /boot partition.

I suggest both an efi partition (UEFI) and a bios_grub (BIOS) partition if not ever installing Windows in BIOS mode using gpt partitioning. Ubuntu will boot from a gpt partitioned drive with BIOS or UEFI.

---

### Post by Aiken Pandora on 2013-04-12
thats sound, yeah wanted to manage it that way with 2 Partitions, but in the moment the Problem is, not matter what I do i can just get it running to boot UEFI. For the Moment it is enough when the system cant boot UEFI and just can boot in BIOS Mode. I used the Live CD to install the BIOS-Grub2 Loader, as i heard, this Bootloader dont need a fully functional MBR, its also works with an GPT (or?).
So my thought was, starting live CD and using Boot-repair to write the Grub2 Loader in the system, so that i can just boot in BIOS (i even erased the UEFI-Loader completly).
But its always the same, when i try to start it in BIOS-Mode the Bootloader doesnt start, the system is just rebooting itself..

With the 2 Partitions, you mean 2 Partitions on the Flash-Drive or on two different drives?

ah what i forgot to say, when i edit the BIOS-Grub Loader installed on another Flash-Drive, i am capable of starting my USB-Flash Drive when i use the Loader of the other system, but i cant get BIOS-Grub2 work on my system.

---

### Post by oldfred on 2013-04-12
gpt is partitioning. UEFI is booting in place of BIOS, but has a BIOS mode for legacy systems that may not work with UEFI. But once Windows is UEFI then you need UEFI for all systems to easily dual boot.

The efi partition with UEFI replaces the MBR in BIOS. The only reason gpt has a protective MBR is to have one partition entry saying the entire drive is gpt, so old partition tools like fdisk do not try to partition it.

The efi partition is like having multiple MBRs in that every install creates its own boot folder and boots from that. It then allows more space so the restriction of a tiny MBR is not there any more. 

If trying to boot in BIOS mode you have to have an install in BIOS mode. It would use the protective MBR for BIOS  type boot code, but you cannot easily dual boot with UEFI. BIOS and UEFI write system data differently to drive for system to boot with.

---

### Post by Aiken Pandora on 2013-04-12
so i would need a MBR Parition for Bios boot?

---

### Post by oldfred on 2013-04-12
The MBR is not a partition, it is just the first sector of a hard drive. BIOS is designed to jump to the MBR to continue booting. Since MBR is just one sector and tiny, it really just links to more boot code elsewhere on drive.

If you have Ubuntu installed run this, or run from your live installer.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

