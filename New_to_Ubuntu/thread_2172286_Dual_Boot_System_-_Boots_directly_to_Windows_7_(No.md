---
title: "Dual Boot System - Boots directly to Windows 7 (No Grub Menu)"
date: 2013-09-04
forum: New to Ubuntu
---

### Post by kirby2 on 2013-09-04
I currently have 6 hard drives:
256GB SSD where Win7 (64bit) is installed. Windows 7 was installed first.
1TB HDD - I shrunk this hard drive by 25GB to make space for Ubuntu (ie a 25GB partition was made on this hard drive)
The other 4 hard drives are just simple storage drives.

My computer runs on a AMD Phenom II x6 1055T CPU so I downloaded the "ubuntu-13.04-amd64.iso" for the installation.

During the install, I selected "Other options" when asked to "Install them side by side", or "Overwrite windows 7 with ubuntu".

When selecting the partitions for installation, I clicked the 25GB free space I had, used 6GB of it for swap and let the remaining 19GB be the mount point "/".
The final option was "Where to install the boot manager". I left it as the default device, sda, which refers to my 256GB SSD where Win7 is installed.

The rest of the installation went on without a hitch and I was prompted to restart. After restarting, my computer booted directly into Windows 7 with no signs of the Grub menu showing up.

Note that before I (re)installed Ubuntu, I tried installing Ubuntu with the "install side by side with windows 7" option. That also resulted with no Grub menu. I tried various random suggestions I found from googling (booting to live cd and trying to install grub by randomly following the commands other typed, etc) but to not much avail. After a few hours of this, I gave up and decided do a fresh install which leads me to this point.

---

### Post by newb85 on 2013-09-04
Boot from the Live CD and install and run Boot Repair.

---

### Post by kirby2 on 2013-09-04
Thanks, it works now :o

It took 20 minutes to get past the "Scanning system. This make take several minutes" message. When I tried boot-repair on the previous install, I clearly gave up too early, thinking the program was hanging.

---

### Post by Quackers on 2013-09-04
LOL, good stuff!
With 6 hard drives to look at there was much to be scanned!

---

### Post by oldfred on 2013-09-04
I have 4 drives and sometimes a flash drive with a full install. I know it takes longer but I assumed it was more that I have many installs for tests on my sdc drive.

I prefer to keep the Windows boot loader on the Windows drive and the grub boot loader on the Ubuntu drive. Then set in BIOS to boot Ubuntu drive. That way if one system or the other stops working then I can use one time boot key or BIOS to boot other system. Also Windows repairs often work best if directly booting Windows rather than thru grub as grub chain boot usually does not give enough time to get to Windows repair console. 

Unless you changed default grub is normally installed to sda. But sda will normally be the BIOS boot drive or first hard drive. But with mulitple hard drives the boot order can change. I skipped a port in SATA port order. Plug in flash drive and it is sde, but reboot with it plugged in, it is sdb and every other drive is one letter more.

---

