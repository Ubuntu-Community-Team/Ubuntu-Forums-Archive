---
title: "Windows not starting after installing Ubuntu"
date: 2018-06-11
forum: New to Ubuntu
---

### Post by rshieh on 2018-06-11
Hi,

I have recently installed Ubuntu and it works great, but now Windows is not starting. I already ran boot-repair, which gave me [this report.]("http://paste.ubuntu.com/p/DcZ4b4zjd8/") The start screen now has several options for system boot---I haven't tried them all, but the ones I tried do not work. I also have already ran "sudo update-grub" on command line and restasted the PC, without success. I have created a system restore point on Windows, but I don't know if I should try to use it (or how yet). Any thoughts?

Thank you very much!

---

### Post by timsdeepsky on 2018-06-11
Greetings rshieh....
I am guessing you have a Lenovo....
Does your start screen have a Windows boot option in your choices?..If so, did you try it?
Are you able to hit F1,or F2 at startup and get into the bios?
If so, do you see any Windows options in the "Startup Device Menu"?
Thank you....

---

### Post by rshieh on 2018-06-11
Hi timdeepsky,

Yes, I have a Lenovo. My GRUB start screen has several boot  options. It only had one Windows option before I used boot-repair, Windows Boot Manager (on /dev/sda2), but now has another 5,  including recovery ones. There's also two EFI/ubuntu/ options, (fwupx64.efi and mmx64.efi). I did try going into all  of them---some just end up on a purple screen and some others go into  Windows 10 automatic repair.

Once I am in Windows Automatic repair, it allows me to return to a system restore point. I suppose I could try to restore it to an earlier point, but I imagine that would uninstall Ubuntu? That would not be a problem, but I want to keep using Ubuntu and it seems that there would be a better solution for that other than reinstalling Ubuntu. I still need Windows for certain specific softwares, otherwise I would ditch it altogether...

I read this problem is related to the HD partition, which I did create when installing Ubuntu, but I couldn't fix it with the solutions I found on forums so far.

Also, I can get in the bios, but the boot options are the same as the grub ones.

Thanks again!

---

### Post by yancek on 2018-06-12
You created an additional EFI partition (sda3) when it was not needed as you already had an EFI partition (sda2) which is what your grub.cfg file is pointing to.    All the correct EFI files for Ubuntu and windows are on sda2.  On my laptop (not a Lenovo), I have an option to boot from EFI file.  If you have that, look for the entry below which is suggested by boot repair:

> Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!] 

Your grub.cfg menu from Ubuntu shows 6 entries for windows.  The one which should boot is the last one listed.  If you hit the e key on your keyboard after highlighting that entry by using the down arrow on your keyboard, you should see the line below at the end of the entry so you know you have the correct one.

> chainloader /EFI/Microsoft/Boot/bootmgfw.efi 

sda3 is useless and not needed.

---

### Post by rshieh on 2018-06-12
I had looked for the shimx64.efi option, but none of options show the file name, both on the BIOS and on the grub menus. On the grub menu, it shows only the options for fwupx64.efi and mmx64.efi files. 

My Ubuntu works perfectly, does that mean it already is booting on the shumx64.efi file? My efibootmgr -v (below) shows the shumx64.efi file on the path of my current boot, but I am not sure if that means anything. Also, I am able to boot on the Windows option you pointed out (it indeed shows the path you pointed out), but it goes to Automatic Repair mode from there.

Thank you very much!


=================== efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0002,0005,2001,2003,0001,2002
Boot0000* EFI USB Device (SanDisk)    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(3,0)/HD(1,MBR,0x5105cc15,0x800,0x1d2d000)RC
Boot0001* Lenovo Recovery System    HD(3,GPT,7e408110-f369-4527-848f-73201a00f564,0x276800,0x1f4000)/File(EFIMicrosoftBootLrsBootMgr.efi)RC
Boot0002* Windows Boot Manager    HD(2,GPT,9211fe45-c39f-4866-9e47-5ac38f21874e,0x1f4800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0003* EFI Network 0 for IPv4 (08-9E-01-F7-23-09)     PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(089e01f72309,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0004* EFI Network 0 for IPv6 (08-9E-01-F7-23-09)     PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(089e01f72309,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0005* ubuntu    HD(2,GPT,9211fe45-c39f-4866-9e47-5ac38f21874e,0x1f4800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

---

### Post by yancek on 2018-06-12
If Ubuntu boot without problems, don't make any changes to it.  The last entry in the Grub menu for windows should show the entry below on screen.  All the other entries are for recovery options and if this one doesn't work, you have some problem with your windows bootloader and I doubt boot repair, Ubuntu or any Linux will be able to help. 

> 'Windows Boot Manager (on /dev/sda2)'

Boot repair does not show your windows Boot directory nor BCD, not sure if that is a problem with windows or boot repair as boot repair 'usually' shows those files.

---

