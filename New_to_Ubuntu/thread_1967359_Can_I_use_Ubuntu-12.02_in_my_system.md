---
title: "Can I use Ubuntu-12.02 in my system?"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by mgrameshbabu on 2012-04-28
Dear Members,
Could any one suggest me to use latest version of Ubuntu-12.02 on my laptop? I have given my system information below. Which version of the Ubuntu is better for my laptop? I need both the OS (Windows-7 and Ubuntu). Is it better to install through wubi or a cd?

Please inform me.

Thanks
Ramesh


System Information:
OS Name	Microsoft Windows 7 Professional
Version	6.1.7601 Service Pack 1 Build 7601

System Manufacturer	LENOVO
System Model	7829BR9
System Type	x64-based PC
Processor	Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz, 2100    Mhz, 2 Core(s), 4 Logical Processor(s)
BIOS Version/Date	LENOVO 8GET33WW (1.10 ), 07-Jun-11
SMBIOS Version	2.6

Windows Directory	C:\Windows
System Directory	C:\Windows\system32
Boot Device	\Device\HarddiskVolume1

Time Zone	India Standard Time
Installed Physical Memory (RAM)	4.00 GB
Total Physical Memory	3.84 GB
Available Physical Memory	2.25 GB
Total Virtual Memory	7.69 GB
Available Virtual Memory	5.83 GB

Page File Space	3.84 GB
Page File	C:\pagefile.sys

---

### Post by Steam. on 2012-04-28
12.04 should be fine.

If you want to remove Ubuntu at a later point without hassle(e.g if you just need it to finish some work), use Wubi.If you want to install it permanently, install it via CD.You'll get an option to install the OS's side by side(later in the install dialogue)and it will replace the Windows bootloader with the GRUB one.

---

### Post by xedi on 2012-04-28
I have a Lenovo Thinkpad x200s which works perfectly out of the box with Ubuntu (also with 12.04) and has somewhat comparable specs. In general Thinkpads are very Linux friendly, so you should be fine.

When you install through CD/USB you have the option to run Ubuntu live from CD/USB and so you could see whether everything works out of the box there, or if you want to be completely sure install it with WUBI and then remove it in case something does not work. As steam said, if you plan to stick with Ubuntu, then installing through CD would be the best option.

---

