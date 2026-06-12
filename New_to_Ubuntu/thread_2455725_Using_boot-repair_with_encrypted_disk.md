---
title: "Using boot-repair with encrypted disk"
date: 2020-12-26
forum: New to Ubuntu
---

### Post by maxime-delorme on 2020-12-26
Hi, 

I am desperately trying to update from a Ubuntu 19 to a 20. Now I had made the transition from 18 to 19 (for various reasons) and di not have any problems. However, time around, it seems that the update has messed with my boot.
I tried to repair grub using Boot-repair (either from the xubuntu live disk after a manual installation; or directly from a boot-repair live usb) but it's not working. Every time I boot, I end up on an initramfs prompt with no information on what went wrong.

Here's the boot-repair log in case you can make sense out of what happened : [http://paste.ubuntu.com/p/PCDBHx7gtF/](http://paste.ubuntu.com/p/PCDBHx7gtF/)

Although my crypted disk and partitions are mounted, boot-repair still displays "[COLOR=#000000]You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]https://help.ubuntu.com/community/EncryptedPrivateDirectory[/COLOR][COLOR=#666666])". I'm not sure if it's of any significance ...[/COLOR]

Now I saw the problem with the encrypted disk, so after running boot-repair, I reran manually the last few steps after modifying /etc/default/grub so that GRUB_ENABLE_CRYPTODISK is set. However it doesn't seem to change anything.

Thank you for your help in advance !

---

### Post by maxime-delorme on 2020-12-26
I fiddled a bit more and managed to have more info printed.
Problem seems to be that the mounting of the root partition is not done when loading grub.

initramfs now tells me :
> ALERT ! /dev/mapper/crypt-root does not exist. Dropping to a shell

However when I look the script grub is running, it is indeed calling to cryptomount.
I am a bit lost and don't really know where to start to solve the problem.

---

### Post by oldfred on 2020-12-26
Do not know encrypted nor LVM installs.

But you have to mount the LVM & decrypt your install as / (root) is inside your encrypted partition. So to make repairs it must be decrypted.

Not sure what Boot-Repair would auto suggest. Often better to use advanced mode and do a full reinstall of grub and latest kernel. Then everything should be updated.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
Shows advanced mode screens.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If Boot-Repair does not work, you can chroot into your install. Some examples, but you have to use your drives & configuration.
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

chroot & troubleshooting Full system encryption
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)

Note that many older (BIOS) instructions may not include mounting the ESP - efi system partition which is required with UEFI installs.

[SOLVED]Secure boot issue - fix with Boot-Repair LVM with encryption
[https://ubuntuforums.org/showthread.php?t=2350963](https://ubuntuforums.org/showthread.php?t=2350963)

---

### Post by maxime-delorme on 2020-12-26
Hi again, 

Thanks for the answer ! It helped me a lot.
I managed to boot finally by decrypting "manually" in the initramfs prompt my disk (cryptsetup open /dev/nvme0n1p4 crypt). 
I need to find now how to do it automatically. Do you know which script allows the mounting of root to be done ? I tried to look for this but all I see is defining stuff in fstab ... which is not what I'm looking for at the moment.

Thank you again !

---

### Post by oldfred on 2020-12-26
Again do not know LVM nor encryption.

I would expect it now is in grub.
Older installs always had /boot outside the LVM, so it could load kernel.
But newer installs now allow /boot to be inside / in the LVM, so it just about has to be a grub driver.
Grub has some drivers included, but many are .mod files that it loads.
I see lvm.mod & luks.mod. 
But if in grub in your /boot folder that is in your install, that would be too late.
I might look at the grub.cfg that is in the ESP.
Mine only has 3 lines & loads the full grub.cfg in /boot folder in /.

The ESP is usually mounted with no permissions in fstab. So you have to mount from live installer to see it. It is then in where ever you have mounted it and /EFI/ubuntu/grub.cfg.
Boot-Repair typically changes the permissions from 0077 to defaults in fstab. Ubuntu used defaults up until 14.04. I assume it could be a security issue as FAT32 does not support Linux ownership & permissions, so to protect it, they now mount with no permissions. I currently manually also change to defaults, but may change back to 0077 in future.

---

### Post by maxime-delorme on 2020-12-26
Actually I'm sorry I should have said that the /boot and /boot/efi are mounted from non-encrypted locations.
The encrypted partition holds the root, /home, /var and /tmp but /boot and /boot/efi are distinct.

---

### Post by oldfred on 2020-12-26
If /var a separate partition, Boot-Repair may not work, or will not automatically work.
It only mounts / & if UEFI /efi. It does find a /boot, but not other system partitions.
Not sure if you manually mount the /var, if then Boot-Repair will work or not.
But either way you have to decrypt install first.

And if chrooting into your system, you also then have to include any separate system partitions like /var also. Tyypical examples of chroot commands only include the typical partitions desktop users normally use. Advanced users that do want separate partitions would know to include those in any repair commands.

---

### Post by maxime-delorme on 2020-12-27
Thanks for the help !
I managed to repair almost everything. I'm still stuck with one last thing (allowing the startup script to automatically decrypt the hard drive) but aside from that I can now start xubuntu and everythign else works perfectly ! 

Thanks again :)

---

