---
title: "Boot Problem Acer E15"
date: 2016-02-25
forum: New to Ubuntu
---

### Post by hughoranga on 2016-02-25
I have a new Acer Aspire E15 with intel N3530 that had Windows 8.1 pre-installed. I'm trying to replace windows with Ubuntu 15.10 and the secure boot thing has got me all messed up. The machine will not reliably boot. It manages to sometimes, and I even remember logging in, but it won't wake from sleep. There was a lot of advice on forums, but I have gotten lost down the rabbit hole, and have resorted to boot repair, which spat out this pastebin address:

[http://paste.ubuntu.com/14473246/](http://paste.ubuntu.com/14473246/)

Any help with this issue would be appreciated.

---

### Post by yancek on 2016-02-26
You have mixed an MBR with a UEFI install and have seen the result.  You have windows files still in the EFI partition and also have the necessary Ubuntu files there.  Unfortunately, you also have Grub code in the MBR which should not be there when you are using UEFI.  You will probably need to reinstall but there may be another solution.  I don't use UEFI myself so don't have any actual experience with it.  You could try overwriting the MBR with instructions at the link below and then try rebooting.  If that doesn't work, you may have to reinsall and you will need to decide if you want to boot/install UEFI or MBR. 

[https://wiki.archlinux.org/index.php/Master_Boot_Record](https://wiki.archlinux.org/index.php/Master_Boot_Record)

---

### Post by hughoranga on 2016-02-26
Thanks for your response. I'm in much deeper than I am comfortable with.  I have only a vague concept of the difference between MBR and UEFI, as  you could probably tell from the pastebin. I looked at overwriting the  MBR but wasn't confident I could follow the instructions, so I have gone  for a reinstall. I dove into the BIOS and switched from UEFI to Legacy,  made sure the USB drive was high in the boot order, and reinstalled  with the erase disk and install option as this talked about setting up  the drive partition, another thing I have a vague notion is important.  This appears to have been successful. I'm guessing this means I have now  have a MBR set up, which is fine by me. I'll test for a bit longer then  mark this as solved if nothing else comes up.

---

### Post by cariboo on 2016-02-27
I have a laptop with the same cpu, what I did is leave the bios alone, used the the Windows disk management tool to create some empty space on the hard drive, then install ubuntu on that empty space. I use the windows boot manager to boot the system either in Windows or Ubuntu. Everything just plain works.

On my considerably more powerful desktop system, 8 core cpu, 16GB Ram and Nvidia GFX-750 graphics card, I originally installed Ubuntu in legacy bios mode, but during the wily development cycle, I decided to try out installing a UEFI system, all it took was using the the manual partitioning option during install to create a 100MB EFI partition, then a / and /home partition, and then doing a regular installation. The system has since been upgraded to Xenial, and has been completely trouble free ever since. The system dual boots Wily and Xenial.

---

### Post by hughoranga on 2016-02-28
I am interested in what you did on your desktop. One thing I haven't  figured out yet in Ubuntu is how to partition. So I don't understand how  to do those slashes there that you mention. This seems to be another  topic, so you might see me start a thread asking how to partition and  format and things, but thanks for your assistance here. The clean "erase  and install" seems to have solved things.

---

