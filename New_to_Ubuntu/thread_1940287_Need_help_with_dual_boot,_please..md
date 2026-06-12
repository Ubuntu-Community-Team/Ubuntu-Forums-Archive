---
title: "Need help with dual boot, please."
date: 2012-03-13
forum: New to Ubuntu
---

### Post by L Campbell on 2012-03-13
I have a Compaq Presario SR210NX  PC with Win XP on a 120GB Seagate SATA hard drive.

What I would like to do is add a 60GB Western Digital IDE hard drive, using UBUNTU, so as to have a dual boot machine.

The machine boots up quite normally into XP and, if I unplug the Seagate hard drive, then connect the WD hard drive, the machine boots up quite normally into UBUNTU.

If, however, I have both hard drives plugged in the machine boots into XP without giving me an option.

FWIW, the WD hard drive will boot whether the Master or Slave connection on the ribbon cable is plugged in.

I would appreciate it if you would tell me what I'm doing wrong.

TIA.

---

### Post by grahammechanical on 2012-03-13
So, far you have done nothing wrong. Which is very important. You still have a working XP install. And you have a working Ubuntu. That is progress.

When we install Ubuntu it puts a boot loader into the Master boot Record (MBR) of the hard disk. If we are installing onto a hard disk with another operating system on it then when this boot loader (called Grub) is activated it searches of other operating systems and creates a boot menu from which we can select which OS to boot into.

When Ubuntu is the only OS on the hard disk, then the boot menu is still created but it is not displayed because there is no need for it to be shown. It knows there is only one OS.

You did well when you installed Ubuntu on its own disk. Now you need to let the Grub boot loader know that there is another operating system present in the machine.

Can you go into the BIOS and select the IDE drive as the first drive to boot from instead of the SATA drive?

Do that and then with both drives in the machine and Ubuntu loaded open a terminal and type

> sudo update-grub

You will be asked to put in your password. It is the password you choose when installing Ubuntu. Nothing will appear on the screen but your typing is still being received. Press enter.

Grub will run a little program that will search for other OS. It will find XP and create a boot menu that will appear when you boot and then you can select either XP or Ubuntu.

To open a terminal. Open the Dash and type

> terminal

I think that this should work.

Regards.

P.S. with IDE drives it is not the position of the connector on the ribbon cable that selects Master or Slave but jumper settings at the back of the IDE drive.

---

### Post by oldfred on 2012-03-13
@grahammechanical
Minor correction. There were at least two versions of IDE. The old versioin was just the jumpers on the hard drive for master slave and used the 40 conductor cable. Then they added another jumper cable select and with 80 conductor cables the position on the cable does determine master or slave.

As soon as SATA became only a few dollars more than PATA I converted to SATA as I made all the mistakes with IDE/PATA you can do. I always had trouble with the tiny jumpers, and they often did not label them well. I tried using a 40 conductor cable with cable select and wondered why it did not work. Evey time I opened computer case I would manage to bump and half disconnect (so it looked connected) the PATA cable. Sometimes drive would light up and just not work.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

---

### Post by L Campbell on 2012-03-13
> **grahammechanical said:**
> So, far you have done nothing wrong. Which is very important. You still have a working XP install. And you have a working Ubuntu. That is progress.

When we install Ubuntu it puts a boot loader into the Master boot Record (MBR) of the hard disk. If we are installing onto a hard disk with another operating system on it then when this boot loader (called Grub) is activated it searches of other operating systems and creates a boot menu from which we can select which OS to boot into.

When Ubuntu is the only OS on the hard disk, then the boot menu is still created but it is not displayed because there is no need for it to be shown. It knows there is only one OS.

You did well when you installed Ubuntu on its own disk. Now you need to let the Grub boot loader know that there is another operating system present in the machine.

Can you go into the BIOS and select the IDE drive as the first drive to boot from instead of the SATA drive?

Do that and then with both drives in the machine and Ubuntu loaded open a terminal and type



You will be asked to put in your password. It is the password you choose when installing Ubuntu. Nothing will appear on the screen but your typing is still being received. Press enter.

Grub will run a little program that will search for other OS. It will find XP and create a boot menu that will appear when you boot and then you can select either XP or Ubuntu.

To open a terminal. Open the Dash and type



I think that this should work.

Regards.

P.S. with IDE drives it is not the position of the connector on the ribbon cable that selects Master or Slave but jumper settings at the back of the IDE drive.

Thanks for your very explicit reply.

I'm having trouble understanding the BIOS as I am not familiar with them so I hope the attached pix will help.

---

### Post by oldfred on 2012-03-13
Did you have both drives plugged in, when you took pictures. It seems to only show one drive not both in hard drive group.

Are drives PATA? Do you have jumpers on hard drives set to cable select and using the 80 conductor cable (multi-color connectors)? 
Or is one drive PATA and one SATA?

---

### Post by L Campbell on 2012-03-13
> **L Campbell said:**
> Thanks for your very explicit reply.

I'm having trouble understanding the BIOS as I am not familiar with them so I hope the attached pix will help.

I see the WD hard drive in the first photo but I was unable to move it and I did not see the Seagate drive.

The 'sudo update-grub' went smoothly and did find the XP OS.

qwer@qwer-P9852A-ABA-753N:~$ sudo update-grub
[sudo] password for qwer: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Windows NT/2000/XP on /dev/sdb2
done
qwer@qwer-P9852A-ABA-753N:~$ ^C

---

