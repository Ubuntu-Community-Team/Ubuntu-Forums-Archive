---
title: "Issues installing dual boot Ubuntu 16.04.3 LTS with Windows 10 PRO 1709"
date: 2017-10-26
forum: New to Ubuntu
---

### Post by iamthecreator on 2017-10-26
Hello, 

I am trying to install Ubuntu 16.04.3 on a Lenovo ThinkStation (with Nvidia Quadro P2000) in dual boot with Windows 10 Pro 1709 already installed.
The first error I ran into was  the following 
"BERT: Can't request iomem region"
I got past this error by changing the "Secure Boot" option in the BIOS
Now I am getting the following error
"nouveau fifo sched_error 08"
Initially it would not even load the Live Ubuntu
I enabled the "nomodeset" set option using the GUI (pressing F6) on the INSTALL UBUNTU screen.
I was able to load the Live Ubuntu
Now when I select the option to install UBUNTU it does not detect the Windows installation (In the past I have installed multiple times and it always detected the current Windows installation and provided the option to install Ubuntu alongside) and wants to format the disk.

Any help will be greatly appreciated.
Please let me know if you need more specific information.

Thanks.
Iam

---

### Post by ajgreeny on 2017-10-26
If this is this a new computer with Win 10 pre-installed it will be using UEFI instead of BIOS.

Did you boot the install USB or DVD in BIOS mode? That is the one possible reason for the system not seeing the Win 10 OS.

Another possibility is that you have left Win 10 fast start (I think that's its name) enabled; this is a hibernated state meaning Linux can not see the partitions even when Windows is shutdown as they are flagged as still in use.

---

