---
title: "Windows not listed in grub!!!  Please help!!!!"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by perro68 on 2012-12-07
I have a toshiba laptop that came with Win8

i partitioned my hard drive because i knew i wanted to install Ubuntu to do a dual boot

after i installed 12.10  the boot menu has no mention of windows


how do i fix this so i can boot into Windows if that is my choice

PLEASE HELP!!!!!

as it stands now when the grub screen comes up

i hit the esc key

i than type exit and the grub> prompt

and i am given a boot screen with boot devices

when i click on the Hard drive i get a boot menu that includes windows

than i wil boot into windows

PLEASE HELP how do i fix this

---

### Post by audiomick on 2012-12-07
Going by your description, everything is there. It sounds like your grub is just a bit messed up.

Have a look here. I would try using this tool
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by oldfred on 2012-12-07
If the computer has Windows 8 preinstall it has UEFI with secure boot. 

Did you turn secure boot off?
Did you turn quick boot or fast boot setting off in UEFI/BIOS?
Does Windows boot from UEFI menu, not grub menu?
Grub2's os-prober has a bug and with efi installs it still creates BIOS type installs which do not work. Again Boot-Repair can create an efi chain load entry. But Windows should boot from UEFI menu directly for chain load entry to work.
How did you resize Windows? Did you use the Windows partition tools and reboot a couple of times before installing Ubuntu? If not Windows may need chkdsk.

Did you use the 64 bit version of Ubuntu and boot it from the UEFI menu in UEFI mode to install? Boot-Repair can convert a BIOS/Legacy install to UEFI.

Best just to post this, if Ubuntu boots or can boot from UEFI menu then you can run it from that or the flash drive you used to install Ubuntu:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by perro68 on 2012-12-08
> **oldfred said:**
> If the computer has Windows 8 preinstall it has UEFI with secure boot. 

Did you turn secure boot off?
Did you turn quick boot or fast boot setting off in UEFI/BIOS?
Does Windows boot from UEFI menu, not grub menu?
Grub2's os-prober has a bug and with efi installs it still creates BIOS type installs which do not work. Again Boot-Repair can create an efi chain load entry. But Windows should boot from UEFI menu directly for chain load entry to work.
How did you resize Windows? Did you use the Windows partition tools and reboot a couple of times before installing Ubuntu? If not Windows may need chkdsk.

Did you use the 64 bit version of Ubuntu and boot it from the UEFI menu in UEFI mode to install? Boot-Repair can convert a BIOS/Legacy install to UEFI.

Best just to post this, if Ubuntu boots or can boot from UEFI menu then you can run it from that or the flash drive you used to install Ubuntu:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

thank you for your replies

i will answer all i can 

i did not turn secure boot off ...actually don't see the option when i get to the boot menu

i did install the 64 bit version ......

my laptop came with Windows 8 and i did partition the disk in windows


when i turn my machine off and restart it

i get a grub menu with no listing of windows

if i hit the esc key and type exit at the prompt

i get to a boot menu ...where if i high light the hard drive i get a menu 

and can choose windows boot record ( i think i am remembering this correctly)

which will get me to windows

i am trying boot-repair now and will report back

---

### Post by perro68 on 2012-12-13
Thanks for the help!!

boot-repair worked perfectly

---

