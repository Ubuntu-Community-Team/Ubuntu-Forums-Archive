---
title: "Dual Booting Ubuntu 15.10 and Windows 7 SP1 (HP Laptop Envy 17)"
date: 2015-11-29
forum: New to Ubuntu
---

### Post by wisemanrax on 2015-11-29
Hi,

I have a laptop that was preinstalled with Windows 7 Pro 64 bit so it came with the SYSTEM, HP_tools, Recovery, and the C: patitions . Before installing Ubuntu 15.10, I deleted the HP_Tools partition (because you can download it again from the HP website again if you wanted to) and I allocated 20 GB for Ubuntu using the Windows disk management tool. I inserted the Live CD (64 bit version) and continued installing. The installation prompted me asking if I wanted to force UEFI mode because my Windows 7 was installed in legacy mode and I said no because I wanted the choice to boot both OS if I wanted to. Ubuntu then detected that I have no other operating systems which is weird so I used the "something else" option and saw the space I allocated and then made sure to mount it to the root and format with ext4. The installation went well and I decided to restart but no grub2 menu showed up. I used the boot repair tool and specified that I wanted Windows 7 to boot by default instead of Ubuntu which was the default choice in the boot repair tool. After this was done, I get a grub2 menu showing Ubuntu, memtest,memtest(serial console), Windows 7 loader sdev1, Windows 7 loader sdev2, and Windows Recovery Evironment. When I choose sdev1, Windows 7 boot normally, but when I choose sdev2, there is a boot error. So my question is, what is sdev2 in this case and what did I do wrong in the first place that resulted in this?

---

### Post by grahammechanical on 2015-11-29
Run Boot Repair again. Get it to produce the Boot report and then paste the URL in your thread. Also, a screen shot of your partitions would be nice, whether taken from Windows 7 or a Ubuntu live session.

Regards.

---

### Post by oldfred on 2015-11-30
Windows 7 and later in BIOS mode, typically has a Boot partition of about 100MB and the main install or c: "drive" partition.  Many Windows users never even see Boot partition nor know it is essential as it has bootmgr & BCD for Windows boot. And then they often just houseclean and delete the sda1 Boot partition.
So Boot-Repair now copies bootmgr & /boot/BCD to main install or sda2. Then grub2's os-prober finds boot files in both partitions as it looks for those boot files to know which partition Windows can boot from. So you end up with two entries in grub.
Most can boot from both, so you may have some issue with your sda2 partition. Post link to Summary report as requested by grahammechanical.

---

### Post by wisemanrax on 2015-12-01
Guys, sorry for the delay in responding but my work wi-fi connection is not allowing me to generate a bootinfo report, it's stuck at netcheck. I will do this when I get home today and connect to my personal network. I've attached a picture of the partition table from the terminal.

---

### Post by yancek on 2015-12-01
windows needs a partition marked as active or bootable.  You can see which partition that is by reviewing the fdisk output you posted which shows an asterisk * under the Boot tab.
windows 7 usually created a small boot partition and a second partition for all the system files which appears to be the case in your situation.  You also seem to have a windows recovery partition and a Linux partition.  No swap but you may not need that.  Post the boot repair output as it will have more details but there doesn't seem to be any problem if you can boot from sda1 as that is the boot partition.  You never indicated if Ubuntu boots which it should if you used Legacy mode to install.

---

### Post by wisemanrax on 2015-12-01
> **yancek said:**
> windows needs a partition marked as active or bootable.  You can see which partition that is by reviewing the fdisk output you posted which shows an asterisk * under the Boot tab.
windows 7 usually created a small boot partition and a second partition for all the system files which appears to be the case in your situation.  You also seem to have a windows recovery partition and a Linux partition.  No swap but you may not need that.  Post the boot repair output as it will have more details but there doesn't seem to be any problem if you can boot from sda1 as that is the boot partition.  You never indicated if Ubuntu boots which it should if you used Legacy mode to install.

Ubuntu runs fine, once I get back home I will post the boot report.

---

### Post by wisemanrax on 2015-12-01
Ok here is the report

[http://paste.ubuntu.com/13609932/](http://paste.ubuntu.com/13609932/)

---

### Post by oldfred on 2015-12-01
Not seeing anything wrong.

You now do have the boot files in both sda1 & sda2, so grub2's os-prober finds both as bootable. And from grub both or either should work as long as Windows is not hibernated nor needs chkdsk. In effect grub only boots working Windows.

Since both Windows & Ubuntu are in BIOS boot mode on a MBR partitioned drive, be sure to only boot in BIOS boot mode. It seems your system is new enough to be UEFI.

---

### Post by mastablasta on 2015-12-02
and don't worry too much about the two entries. just use the one that works well (if only one works).

by the way you didn't have to delete any partitions, as you could have just made one of them a secondary partition. 

20GB is not much space, but I guess it will do for some basic usage.

---

### Post by wisemanrax on 2015-12-02
Great thank you! One more question though. What is sdev/ram00-15 for? I see that whenever I run sudo fdisk -l . It totals to 1 GB of RAM but for what reason?

---

