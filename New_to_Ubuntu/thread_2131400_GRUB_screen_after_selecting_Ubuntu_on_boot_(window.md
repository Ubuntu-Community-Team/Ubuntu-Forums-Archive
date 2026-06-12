---
title: "GRUB screen after selecting Ubuntu on boot (windows 7 computer)"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by PieEconomics on 2013-04-01
I have windows 7 and Ubuntu 12.10. It has been working great for months; I just select Ubuntu when prompted during boot.
When I selected Ubuntu today, however, I got a screen that says "GRUB". Do I have to enter something at the GRUB prompt to get my Ubuntu back?

---

### Post by oldfred on 2013-04-01
You normally get the grub> error after BIOS. Is this a wubi install where you select Windows or Ubuntu in the Windows boot screen?

Post this from a Ubuntu liveDVD or flash drive terminal:

sudo fdisk -lu

---

### Post by PieEconomics on 2013-04-01
Yes, this is a wubi install, and when I select Ubuntu instead of Windows 7, I get the GRUB prompt.
Should I enter "sudo fdisk -lu" at the GRUB prompt?

---

### Post by nerdtron on 2013-04-01
> **PieEconomics said:**
> Yes, this is a wubi install, and when I select Ubuntu instead of Windows 7, I get the GRUB prompt.
Should I enter "sudo fdisk -lu" at the GRUB prompt?

Nope. Run a LIVE CD or boot from a USB stick, open a terminal window and enter the command.

---

### Post by oldfred on 2013-04-01
I needed to know if wubi or full partitioned install as running fsck it different. You also may need to run chkdsk from Windows. Wubi is just a large file inside the NTFS partition. That file internally is a Linux format and probably needs fsck. You need to run fsck from a liveDVD or Flash drive not from Windows.

 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

If you so not have a live installer you need one.

 Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

