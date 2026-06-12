---
title: "How do I discern which Partition has Grub and boot record ..."
date: 2024-01-09
forum: New to Ubuntu
---

### Post by cwmoser on 2024-01-09
How do I discern which Partition has Grub and boot record?

The reason I am asking is that I have 3 hard drives:
/dev/sda, /dev/sdb, and /dev/sdc

My bootable partition is /dev/sda4

I had a failure with /dev/sdb which prevented my Ubuntu OS from booting ... just drops to terminal with errors.

I finally got everything working using my Ubuntu Mate Install USB, dropping to Terminal and editing /etc/fstab removing the /dev/sdb emtry.

---

### Post by oldfred on 2024-01-09
If UEFI it is probably the ESP on sda.
If old BIOS, it is the drive you have specified as default boot.

If you want details:
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I periodically run the report & save a copy in /home so included in my backups, just to document system. 
Copy normally in /var/log/boot-repair along with some of its other files.

Note that other parts of grub are in /. 
1. /etc/default/grub - the file containing GRUB 2 menu settings.
2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

---

### Post by cwmoser on 2024-01-10
Thanks @oldfred.  I put that information in my Ubuntu notes file.

---

