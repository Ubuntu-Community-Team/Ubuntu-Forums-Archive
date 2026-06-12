---
title: "Avoiding grub in windows bootloader"
date: 2020-04-15
forum: New to Ubuntu
---

### Post by inappropriate on 2020-04-15
Hello and thanks in advance. Is there any way to avoid grub being installed on the WIndows bootloader? I find that ubuntu is writing to the bootloader even when it is not asking me about it.

For example, I'm running two SSDs in my laptop. I removed the SSD that has Windows on it and installed Ubuntu on the 2nd SSD. I then installed the 1st SSD back again. Everything was great as the computer would boot directly into Ubuntu and I could launch Windows via BIOS when I wanted to, which was the desired state. However, I did a software update in Ubuntu and restarted only to find the dual boot now on my computer, with grub written to the WIndows boot loader. Is there any way in having Ubuntu stay the hell away from my Windows bootloader?

---

### Post by oldfred on 2020-04-15
I do not know how grub would have installed to Windows drive, unless you did a total uninstall/reinstall of grub.
What UUID do you have in fstab vs UUID of both ESP?
cat /etc/fstab
lsblk -o name,fstype,size,fsused,label,uuid,mountpoint

---

### Post by crip720 on 2020-04-15
Think he had a grub update when second SSD with windows was connected and grub pickup the windows OS.  I am not sure how bootloaders works, but the OP now has grub showing up as primary.  Think there is a way to prevent 'OS Prober" from working, but need someone else to explain.

---

### Post by oldfred on 2020-04-15
If you do not want Windows in grub menu, you turn off os-prober.
A couple of ways, add an entry to grub or turn off execute bit on the os-prober part of grub update.

In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executable bit, so not run when grub updates.
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by Impavidus on 2020-04-16
Ubuntu or grub did not write anything to the Windows boot loader. It only created an entry for Windows in grub, the Linux boot loader. If you remove one the drives, you'll see that the system on the other drive still boots. If you don't want that (I don't see why), you can disable the OS-prober.

---

