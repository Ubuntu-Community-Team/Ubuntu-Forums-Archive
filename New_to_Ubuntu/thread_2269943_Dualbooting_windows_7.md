---
title: "Dualbooting windows 7"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by FROG_ on 2015-03-19
i have installed ubuntu, is it possible to dual-boot ubuntu with windows 7 ??

---

### Post by Vladlenin5000 on 2015-03-19
Hello and welcome.

It surely is but it's much easier to install Windows first. Depending on the machine (old BIOS or new UEFI) it may not be a task for newbies...

---

### Post by benrob0329 on 2015-03-19
It is, But you will want to install Windows 7 first. Windows is made to see Windows, not Ubuntu. Where Ubuntu is made to both Ubuntu and Windows, as well as other OSes too. 
What I mean by "see" is to recognize the other OS already installed on your hard drive. 

1. So you should install Windows over Ubuntu, then shrink your Windows partition. [https://technet.microsoft.com/en-us/magazine/gg309169.aspx](https://technet.microsoft.com/en-us/magazine/gg309169.aspx)

2. Then go to install Ubuntu, but select the "Install Alongside Windows 7" option. 

2.5. If it's not there, then select the "Something Else" option. When you see the partitions on your hard drive:

[LIST=1]
[*]Make a new one as a primary partition starting at the beginning of the empty space. Leave enough space for swap (a little bigger than the size of your ram), format it with the EXT 4, and mount it to "/"
[*]Make another partition, with what space is left on your hard drive, and format it as "Swap Area".
[*]Finish installing Ubuntu
[*]Do a Boot Repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[/LIST]

---

### Post by oldfred on 2015-03-19
Main question is system newer UEFI or older BIOS?
And then how you install is different, but primarily that you must boot Windows 7 installer in same boot mode as Ubuntu is installed. 
If you have gpt partitioning but booting Ubuntu in BIOS mode, you cannot easily install Windows as it has to be in UEFI mode with gpt partitioning.
If older BIOS system with MBR partitioning, Windows must be installed to a primary NTFS formatted partition with boot flag.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

