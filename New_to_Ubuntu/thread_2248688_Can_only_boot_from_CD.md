---
title: "Can only boot from CD"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by lascuba on 2014-10-16
So a few weeks ago I installed  32-bit Linux Mint 17 on a brand new laptop. I followed general instructions for installation rather than the specific ones for UEFI, and I ended up with a linux os that was working fine but I had issues with Windows. Since I hate Windows 8 anyway I went ahead and got rid of it and installed the 64-bit Mint. I haven't been able to boot from my hard drive since. I've reinstalled Mint multiple times, I've tried reinstalling grub following direction in these forums with no success--almost any command that includes "grub" gives me a "failed to get canonical path of /cow" error message. (I posted details in the Mint forums--let me know if it's ok to link). I tried installing rEFInd and I got this:
> 
Notice: Backed up existing icons directory as icons-backup.
Existing refind.conf file found; copying sample file as refind.conf-sample
to avoid overwriting your customizations.

cp: cannot overwrite directory ‘/boot/efi//EFI/refind/refind.conf-sample’ with non-directory
rEFInd has been set as the default boot manager.
Creating /boot/efi/boot/refind_linux.conf; edit it to adjust kernel options.

ALERT:
Installation has completed, but problems were detected. Review the output for
error messages and take corrective measures as necessary. You may need to
re-run this script or install manually before rEFInd will work.

Finally I tried installing Ubuntu and, just like since installing 64-bit Mint, when I try to boot I get  

"Reboot and Select proper Boot device or Insert Boot Media in selected Boot Device and press a key."

My laptop is in UEFI mode, secure boot off, set to boot from hard drive. I have no idea what else to do. Any ideas?

---

### Post by irv on 2014-10-16
First thing you need to do is boot into your BIOS and check your boot 
Make sure you are booting from where your grub is.
Your BIOS will look something like this.
[http://www.clearcenter.com/support/howtos/configuring_a_bios_boot_device]("http://www.clearcenter.com/support/howtos/configuring_a_bios_boot_device")

---

### Post by stalkingwolf on 2014-10-16
i d bet you need to disable the uefi mode and use legacy as i recall.> My laptop is in UEFI mode, secure boot off

---

### Post by lascuba on 2014-10-16
> **stalkingwolf said:**
> i d bet you need to disable the uefi mode and use legacy as i recall.

I tried it once after one of the many renistalls and it didn't work. I'll try it again when I get the chance, because why not.

---

### Post by frank75 on 2014-10-16
I would try disabling UEFI, enable Legacy and boot to a USB stick with Ubuntu on it(if you can) and use Disks or gparted to totally reformat the hard drive so it'll be squeaky clean with nothing on it except one ext4 partition. That'll get rid of any remnants of Windows and get things ready for a new install. Then install Ubuntu, boot to your new system and do your "sudo apt-get update" and "sudo apt-get dist-upgrade" to make sure you've got all the newest packages and see if you can then boot to your Optical Drive.

---

### Post by JeQhdMD on 2014-10-16
Before doing anything else, my suggestion would be to check if you did the 64 bit install correctly, including having "fast boot" OFF, UEFI enabled and "secure boot" ON.  BTW, some hardware models "require" Windows present . . . uninstalling it on those machines is not recommended, although dual-boot will work fine.

---

### Post by oldfred on 2014-10-16
Post link to summary report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What brand, model system?
Some require boot parameters for video or other hardware. And if you only have one install, grub menu will not show be default. If UEFI you have to press escape to get menu or if BIOS hold shift key from BIOS until menu appears.

Also some vendors (HP, Sony a few others) modify UEFI to only boot Windows or a hard drive, but not any UEFI entry that does not say Windows. You have to then do a work around to get grub as the hard drive entry.

---

### Post by lascuba on 2014-10-16
I didn't expect it work at all but I just enabled legacy and then reinstalled and now it's booting fine.  Everything I read said to install in UEFI mode. I'm equal parts relieved and want bang my head against a wall that such a simple thing worked.

Thank you.

---

### Post by frank75 on 2014-10-16
It's crazy that sometimes such a little tweak can make things just work.  I'm glad you were able to get things up and running.

---

### Post by BlinkinCat on 2014-10-16
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

