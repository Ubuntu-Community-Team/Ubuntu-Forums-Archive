---
title: "Trying to Dual Boot with HP Laptop and Windows 10"
date: 2019-09-26
forum: New to Ubuntu
---

### Post by choadles on 2019-09-26
Hey all,

I'm very new to this and I've been on multiple websites and forums taking alot of advice but I'm still having trouble trying to get my HP Laptop to boot into GRUB so I can choose to boot into windows from GRUB or let it automatically boot up Ubuntu. 

Currently I have Secureboot turned off and Legacy mode turned off. I've fully deleted all my partions and installed Ubuntu on it's own so it would create the boot partition. Then I shrunk the ext4 partition and created a Fat32 partition for Windows 10 install. Restarted the computer with a Windows 10 USB inserted and successfully installed Windows 10 on that partition. The only problem is that windows overwrote the EFI files (I think - that's what it sounds like). Others have posted that you have to move the efi files from the Ubuntu folder on the boot partition to the Microsoft boot folder as my laptop is an HP and has the HP UEFI firmware which doesn't allow you to choose which to boot from the BIOS menu.

The problem I'm having is that the commands given on one of the forums mention to boot Ubuntu into a live session, mount the boot partition and then move the files but I'm getting a permission denied error. I've also tried running the Boot-Repair from a live session with Ubuntu and it fails out. I have a boot log that they provided when I received the error which I have below.

ANY help would be greatly appreciated. I've also tried to load cmd in windows to bcdedit but I hear that doesn't work with HP laptops.
Thank you SO much in advanced.


[http://paste.ubuntu.com/p/8nbGs2cQSw/](http://paste.ubuntu.com/p/8nbGs2cQSw/)

---

### Post by yancek on 2019-09-27
You don't need a separate boot partition and the boot repair output does not show a separate boot partition but does show an EFI partition.  It looks like you have installed Ubuntu at least twice as you have Grub boot code in the MBR which is the result of a Legacy install, as well as the Grub EFI files on the EFI partition (sda1).  With Legacy disabled in the BIOS firmware, it should go to the EFI partition to boot.  You can see in the boot repair output that you have separate directories for windows and Ubuntu (ubuntu, microsoft) which have the necessary boot files for the respective OS.  Windows did not overwrite your Ubuntu EFI files, they are shown on sda1.

The boot repair output generally shows Grub files including the menu file that you would see on boot, grub.cfg.  That does not show in the boot repair output on the Ubuntu partition (sda2) so I don't know if it does not exist or if it is simply not detected by boot repair.   Boot the Ubuntu install usb and in a terminal, mount the Ubuntu partition (sda2) and navigate to the /boot/grub directory to see if you have a grub.cfg file.  There is a grub.cfg file on the EFI partition but that does no more than point to a grub.cfg file which should be on sda2.  If you don't have a grub.cfg file on sda2, you need to either re-install Ubuntu EFI or re-install grub efi.

Take a look at the documentation at the Ubuntu site below which explains in detail dual booting windows 10 and Ubuntu UEFI.  Read this 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

On my HP laptop, when it boots I hit the Esc key to get options.  There is a boot option key (F9) which allows selection of an OS and there is an F10 option which allows changing the BIOS firmware setting to permanently change which to boot by default.  There is also an option to "boot from EFI file".  Do you not have these options?  These options will all fail if you do not have a grub.cfg file on the Ubuntu partition (sda2).

---

### Post by jeremy31 on 2019-09-27
My HP laptop has System Configuration in BIOS and I have to use the OS Boot loader option and put ubuntu on the top of that list and save for it to boot into grub rather than directly into Win 10

---

### Post by choadles on 2019-09-27
Thanks Jeremy - I've seen that on other posts about hitting enter when you have OS Boot Loader highlighted and then you can choose which OS to boot into and move it to the top, but I guess my laptop being from 2013 doesn't have the ability. I even updated my BIOS but I don't believe that was the problem.

And thanks Yancek - I'll take another look at that page after. You're also right in the fact that I did install Ubuntu in Legacy mode at least once as I did see that screen one of the times I was installing. I will check on the ubuntu option for the grub.cfg file and try to reinstall grub efi or Ubuntu EFI later on tonight to see if any of that may work. I also have the option to hit Esc or F9 and choose to boot into Ubuntu at startup - I just wanted to have Ubuntu be my primary OS and have GRUB boot up initially instead of Windows OS booter by default and maybe it's the age of my HP laptop but as I mentioned to Jeremy I don't have the option to permanently change the OS boot loader to Ubuntu rather than to windows. It sounds like I need to modify the EFI files to make shim or grubx64.efi renamed to the windows .efi file so BIOS thinks it's booting windows by default. I'll report back once I have a chance to check the grub.cfg

Again - thank you both for commenting - very new to this but definitely want to start getting better with coding, etc.

---

### Post by Frogs Hair on 2019-09-28
I use [Easy BCD]("https://neosmart.net/EasyBCD/") which gives me grub and also and the metro boot loader. My reason is that Windows would not complete major updates without the Windows boot loader. I also use the grub customizer from the repository to change the boot order and it also has resolved grub overwrites to the Windows option.

```
HP Compaq 8460p USAO  Legacy Bios
```

---

### Post by choadles on 2019-09-28
Hello all,

Again, I 100% appreciate all the solutions provided - I finally figured it out.  I was on the right page but not quite there. Because of the model of the HP laptop I have, I couldn't modify the OS Boot Loader to load Ubuntu instead of Windows Boot Loader. So I had to replace the bootmgfw.efi with the the grubx64.efi file. it worked PERFECTLY. Unfortunately my laptop BIOS cannot deal with switching the main EFI file with an Ubuntu file, I had to force it to think it was loading the windows boot loader. The link I followed was below. You guys are awesome - I appreciate the experience. 

I feel the reason I couldn't swap the files initially with the "permisson denied" error was because I didn't type sudo before I was trying to move files. Getting there slowly.

[https://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](https://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

---

### Post by r_widell on 2019-09-28
My old HP Elitebook 8470P would only boot Windows, no matter what I tried. So I had to brute-force it (more on that later).

The Super Grub2 boot disk, found among other places on the [Ultimate Boot CD]("https://ultimatebootcd.org")  has been very handy in booting up a system where the bootloader has been corrupted or not installed. If you can boot from optical media or USB thumb drive, that should get you into you OS so you can install/repair the bootloader.

But what I had to do on my Elitebook was move some files around. In your ESP (normally /dev/sda1), under the directory /EFI, you should find a directory for each of your installed OS'. e.g. Microsoft, ubuntu as well as a directory named Boot. In that Boot directory is a file named bootx64.efi.

Rename that file to MS-bootx64.efi. Then copy grubx64.efi from the ubuntu directory and put it in the Boot directory as bootx64.efi.

You have now replaced the MS bootmanager with GRUB. When your system boots up into GRUB you will be able to select which OS you want to boot, assuming that grub.cfg exists and os_prober has been enabled.

N.B.- some distros, notably openSUSE, ignore everything in /etc/default/grub and the files in /eyc/grub.d when a new kernel is installed. A new initrd/initramfs and  a new grub.cfg is built, but the only OS you'll see on the reboot is that for the newly installed kernel. You'll need to manually make a new grub.cfg ```
#grub-mkconfig -o /boot/grub[2]/grub.cfg
```
Good luck,
ron

---

