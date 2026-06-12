---
title: "How to repair &quot;IOError: [Errno 13] Permission denied: 'F:\\wubildr'&quot;"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by jackn703 on 2011-11-08
Tried installing wubi on a new HP Pavilion p7-1120 from [here]("http://www.ubuntu.com/download/ubuntu/windows-installer"). Get 
> Ubuntu Installer - An error occurred: Permission denied. For more information please see log file ...\wubi-11.10-rev245

The last line in the log file is 
> IOError: [Errno 13] Permission denied: 'F:\\wubildr'
I tried to upload the full log file as an attachment to the forum but got the following complaint: 
> Your file of 57.4 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.

How do I fix the IOError?

_HP Pavilion p7-1120 Specs_
Processor: Intel Core i3-2130 3.4 GHz, DMI 5GT/s
Chipset: Intel H61
Memory: 8 GB DDR3
HD: 1.5 TB SATA
Optical drive: SuperMulti DVD Burner
Graphics: Intel HD Graphics (up to 1.69 GB)
Video connectors: 1 DVI; 1 VGA
Network interface: On-board 10/100/1000Mbps Gigabit Ethernet

---

### Post by Mark Phelps on 2011-11-08
Did you run the installer as Administrator?  Could be that it needs elevated permissions to make changes in the boot loader info.

---

### Post by philinux on 2011-11-08
Can you run ubuntu even though the error message got displayed.

Bug here.
[https://bugs.launchpad.net/wubi/+bug/862003](https://bugs.launchpad.net/wubi/+bug/862003)

---

### Post by Rubi1200 on 2011-11-08
It would also be worthwhile checking the Windows Disk Management utility to see if your disks are labeled as Dynamic or Basic.

I suggest you also check the MD5SUM of the ISO:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Another common solution is to place the wubi.exe and downloaded image in the same folder before running the executable.

---

### Post by gautam_jat on 2011-11-08
even i had the same problem like u.I tried much but of no use.Then finally i downloaded the iso again and everything went fine.
so i suggest u to download the iso, i think ur iso was corrupted, as was mine.
and after downloading the new iso, when it again displays the same error, press ok, and try again and again, and it will work for sure as it worked for me too.
Usually iso gets corrupted when we pause and restart iso downloading many times in download managers.
I am a begennier using ubuntu for 4 months and this was how i sorted out this problem.

---

### Post by gautam_jat on 2011-11-08
[]("http://www.ubuntu.com/download/ubuntu/windows-installer")and I/O error is caused when ur computer is unable to read data from optical disk or any other external hardware.As it rely on the drive letters of ur system.
if i m not wrong then i think F is ur optical drive.

---

### Post by jackn703 on 2011-11-08
> **philinux said:**
> Can you run ubuntu even though the error message got displayed.

Bug here.
[https://bugs.launchpad.net/wubi/+bug/862003](https://bugs.launchpad.net/wubi/+bug/862003)

Damn! It was such a scary looking error message I didn't think to check. Looks like it runs just fine.

---

### Post by philinux on 2011-11-08
> **jackn703 said:**
> Damn! It was such a scary looking error message I didn't think to check. Looks like it runs just fine.

Sweet. :P

---

### Post by Rubi1200 on 2011-11-09
> **jackn703 said:**
> Damn! It was such a scary looking error message I didn't think to check. Looks like it runs just fine.

Excellent! Glad you got things sorted out and can enjoy Ubuntu :)

---

