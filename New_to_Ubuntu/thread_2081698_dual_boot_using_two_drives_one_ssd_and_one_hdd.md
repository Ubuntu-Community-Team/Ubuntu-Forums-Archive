---
title: "dual boot using two drives one ssd and one hdd"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by Inspector Gadget on 2012-11-07
I have a 120gb SSD which boots straight into Ubuntu 12.04LTS and another 320gb HDD dual booting XP sp3 and 12.10 (which keeps crashing at the login screen), I would like use the SSD as my primary drive with the option to boot XP on the HDD as and when. At present I connect the SATA cable for whichever drive I intend booting but is is possible to connect the SSD to SATA1 and HDD to SATA3 with the choice to boot either? I have looked at the 'Grub Tutorial' but its a bit beyond my meagre PC talent, I can open the terminal and ask it questions... any help gratefully received, thanks..

Les

---

### Post by grahammechanical on 2012-11-07
I am not sure that I have the answer but I was thinking about this very subject the other day when I was looking at SSDs in a computer shop.

I suggest that you examine the BIOS set up program for your machine. It seems logical that the boot process would look first at sata port 1 before it looks at sata 2, 3, etc. But I think that you can set the boot order in the BIOS.

Next if you boot into Ubuntu (12.04) on the SSD and run

```
sudo update-grub
``` with both disk drives connected, then a script will run that will search for all the operating systems on your drives. It will configure a boot menu that will be put in the Ubuntu (12.04) on the SSD.

Then, when you boot the BIOS it should first look to the SSD and find a Grub boot menu which will list those three operating systems that you have in the machine.

This is how I reason it out.

Regards.

---

### Post by oldfred on 2012-11-07
I had to stop booting XP when I installed my SSD. But I had said for 5 years I was going to stop and it finally forced me. :)

XP does not really have AHCI drivers and with SSD you have to use AHCI if you want trim to work. Or else SSD will get slower & slower. You can install AHCI driers into XP with a new install. I did find instructions to install after the fact but it was so complex, I just figured it was time to give up on XP.

XP's boot.ini is hard coded to which drive & partition it is in. So if you start changing that around you have to edit boot.ini. Somewhat like Linux was before UUIDs when it used device like /dev/sda1 and then you changed drive order.

I used Ubuntu in sdb & sdc with XP in sda for years. Until I added SSD, I had no real issues dual booting.

Have your run?

sudo update-grub

You may just want to post the link to BootInfo.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Inspector Gadget on 2012-11-07
Thats perfect, thanks Graham, all I need to sort out now is the login screen issue and I'll be a happy bunny lol, by the way 4 seconds from grub to loaded on the SSD so thats a bonus... thanks
#
#> **grahammechanical said:**
> I am not sure that I have the answer but I was thinking about this very subject the other day when I was looking at SSDs in a computer shop.

I suggest that you examine the BIOS set up program for your machine. It seems logical that the boot process would look first at sata port 1 before it looks at sata 2, 3, etc. But I think that you can set the boot order in the BIOS.

Next if you boot into Ubuntu (12.04) on the SSD and run

```
sudo update-grub
``` with both disk drives connected, then a script will run that will search for all the operating systems on your drives. It will configure a boot menu that will be put in the Ubuntu (12.04) on the SSD.

Then, when you boot the BIOS it should first look to the SSD and find a Grub boot menu which will list those three operating systems that you have in the machine.

This is how I reason it out.

Regards.

---

### Post by Inspector Gadget on 2012-11-07
hello 'oldfred'

this boot repair from this afternoon when I unplugged the SSD and lost access to grub...

[http://paste.ubuntu.com/1339908/](http://paste.ubuntu.com/1339908/)



I'm sticking with XP I guess until MS stop support totally and I hope never to have to buy another MS OS in the future...

thanks for the help..

Les

---

### Post by oldfred on 2012-11-07
You are showing wubi, which boots from the Windows boot loader and adds an entry into boot.ini. The grub menu is more for similarity with a standard full install. 

Do you have a full Ubuntu install on another drive?

---

### Post by grahammechanical on 2012-11-07
>  I unplugged the SSD and lost access to grub...

Ah. That says that the Ubuntu 12.04 Grub menu is on the SSD. Which is what you want, I think. With the SSD as the first drive to boot from do you get a grub menu to gives an option to boot XP on the other drive? If so, equals success.

As I was looking at the SSDs in that shop I was wondering if they have the same connectors as Sata drives. Is it as simple at that to install a SSD?

Regards.

---

### Post by oldfred on 2012-11-07
I bought a Microcenter SSD almost a year ago. As the house brand it was a bit cheaper, but since then SSDs have come down in cost a lot.

My motherboard has SATA connectors and I just had to plug it in. It did not include adapters to fit into my 3.5" cage on Desktop as it was 2.5", but all the wiring is just standard SATA signal & power.

Standard install to a second drive with a few settings to reduce writes. I use just as boot drive with data still on rotating drives. Boot is fast, but I cannot type any faster, so it did not help me there.

---

