---
title: "boot-repair"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by gcas on 2012-07-08
I manually upgraded to xubuntu 11.10 and now I'm unable to boot my windows xp again.
I run update-grub but nothing happened, so I tried boot-repair with the "Recommended repair" option without success. The corresponding output is in [http://paste.ubuntu.com/1081072/](http://paste.ubuntu.com/1081072/)
No partitions were overwritten, and I am able to reach all the info in the windows HD.
Any tips?

---

### Post by Gone fishing on 2012-07-08
I've always been quite fond of GAG [http://gag.sourceforge.net/index.html](http://gag.sourceforge.net/index.html) you would need to reinstall grub onto the root of your Ubuntu root partition (sda5) and then GAG onto the MBR.

---

### Post by drs305 on 2012-07-08
gcas,

Welcome to the Ubuntu Forums.  :-)

I'm not a Windows user but in my basic review of the info things look fairly normal.

How does your Windows boot fail? Do you see the GRUB menu, do you see the Windows entry, what happens when you select Windows and attempt to boot?

Same question about update-grub?  What do you mean "nothing happened"? Did the command run, did you see output in the terminal, did it appear to find Windows, etc? There is a 30_os-prober section of the grub menu and a Windows listing, so it appears that it found Windows, at least at some point.

---

### Post by gcas on 2012-07-08
Thank you guys or your quick reply!
> **drs305 said:**
> How does your Windows boot fail? Do you see the GRUB menu, do you see the Windows entry, what happens when you select Windows and attempt to boot?

Yes, I can choose from the GRUB menu the Windows entry, but when I do that, an empty screen appears and I can so nothing else but reboot...

> **drs305 said:**
> Same question about update-grub?  What do you mean "nothing happened"? Did the command run, did you see output in the terminal, did it appear to find Windows, etc? There is a 30_os-prober section of the grub menu and a Windows listing, so it appears that it found Windows, at least at some point.

The update-grub command run perfectly, and the output is

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-22-generic
Found initrd image: /boot/initrd.img-3.0.0-22-generic
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

So you're right, the Windows entry is right there.

I will see something about GAG and will let you know...

---

### Post by drs305 on 2012-07-08
If you don't want to wait for input from Windows users, you can change the bootloader back to Windows. If the problem is with GRUB, this should allow you to at least boot Windows. If it doesn't work with this 'fix', at least you will know that the problem is with your Windows files.

If you want to try it:
Boot into Ubuntu.
Install *lilo*, an alternate bootloader.
Point the MBR back to the Windows partition. Do NOT run the lilo configuration commands - just the ones below. 
Reboot and you should get your Windows bootloader.
```

sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot to Windows.

If it doesn't work, boot a LiveCD and run the following commands to restore GRUB. Do NOT use the partition number in the second command:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /dev/sda5

```
Reboot

---

### Post by oldfred on 2012-07-09
These are the standard Windows XP repair commands. You probably need either fixBoot or chkdsk as grub2's os-prober did find your install.

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

You can use Boot-Repair or these commands to restore grub2's boot loader once Windows boots on its own directly.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by gcas on 2012-07-22
> **drs305 said:**
> If you don't want to wait for input from Windows users, you can change the bootloader back to Windows. If the problem is with GRUB, this should allow you to at least boot Windows. If it doesn't work with this 'fix', at least you will know that the problem is with your Windows files.

If you want to try it:
Boot into Ubuntu.
Install *lilo*, an alternate bootloader.
Point the MBR back to the Windows partition. Do NOT run the lilo configuration commands - just the ones below. 
Reboot and you should get your Windows bootloader.
```

sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot to Windows.

If it doesn't work, boot a LiveCD and run the following commands to restore GRUB. Do NOT use the partition number in the second command:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /dev/sda5

```
Reboot

Hi guys, I'm back.
I tried to change the mbr, but windows fails to start (I get a blank screen). I had to restore grub then, as suggested, and returned to the situation at the beginning: I can choose through grub to boot my ubuntu, but when I choose to boot in Windows, I get that blank screen again...

---

### Post by YannBuntu on 2012-07-28
Have you tried the commands suggested by oldfred? (FIXBOOT ...)

---

