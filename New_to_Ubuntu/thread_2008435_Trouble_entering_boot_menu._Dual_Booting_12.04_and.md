---
title: "Trouble entering boot menu. Dual Booting 12.04 and Win7"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by Mithost on 2012-06-22
I installed windows 7 first, had it on for 2 and a half months, then I decided to install Ubuntu 12.04. I installed it from the live CD fine, but when I restart the computer, windows 7 loads like normal. First time it booted it asked for a disk check which I allowed to happen. I've trying holding/pressing/tapping shift during booting, but I just get windows 7. No altered coloured ubuntu screen, no small GRUB text, nothing different.

Ubuntu is installed on a second hard drive from Windows 7, C:\ Drive given to Windows and my E:\ Drive is Ubuntu. The second drive was formatted before installation.

I would like to keep Windows 7 as my default OS, without a menu automatically appearing. This is so my computer-illiterate family will not get confused. I just want to know what button can enter the GRUB menu so I can choose to boot Ubuntu instead of Windows. I cannot access Ubuntu in any way that I know of right now. Please help!

---

### Post by anewguy on 2012-06-22
Please see [this]("http://ubuntuforums.org/showthread.php?t=2008059") thread - I think it will help you.

---

### Post by jmfal on 2012-06-22
Windows loads no matter what you do because you have it set at #1 boot priority,  you said that is what you want.
Restart> at bios/setup screen there should be a option to enter boot menu> select bootmenu>  select your ubuntu hdd> press enter>then tap/hold down shift key .

That should bring you to the grub screen.
If it boots straight into the login screen thats ok  you have a working ubuntu.
Check in software center and see if grub is installed. IF not open a terminal and enter
```
  sudo apt-get install grubpc
```
Then```
sudo apt-get upgrade
``` and```
sudo apt-get upgrade
```
Enter first command the press enter and enter password at prompt it is hidden for security reasons the enter the other commands pressing enter after each one

---

### Post by jmfal on 2012-06-22
I'm sorry the second command is
```
  sudo apt-get update
```

If it boots to your grub screen then select recovery kernal and the update grub selection

It may ask for username and password

---

### Post by anewguy on 2012-06-22
The link I posted covers all of this and more.

---

### Post by wilee-nilee on 2012-06-22
> **Mithost said:**
> I installed windows 7 first, had it on for 2 and a half months, then I decided to install Ubuntu 12.04. I installed it from the live CD fine, but when I restart the computer, windows 7 loads like normal. First time it booted it asked for a disk check which I allowed to happen. I've trying holding/pressing/tapping shift during booting, but I just get windows 7. No altered coloured ubuntu screen, no small GRUB text, nothing different.

Ubuntu is installed on a second hard drive from Windows 7, C:\ Drive given to Windows and my E:\ Drive is Ubuntu. The second drive was formatted before installation.

I would like to keep Windows 7 as my default OS, without a menu automatically appearing. This is so my computer-illiterate family will not get confused. I just want to know what button can enter the GRUB menu so I can choose to boot Ubuntu instead of Windows. I cannot access Ubuntu in any way that I know of right now. Please help!

If ubuntu put grub in the mbr of that second drive just find the per-session boot key, mine is f12, for a out of the bios boot from menu.

You could let grub have the boot from that drive and put W7 first to boot if you want, with the grub customizer, and keep the windows bootloader in its HD's mbr.

Just options here, the first meets your request, just find the correct key or keys for this menu option, it is run as if you were going to the bios.

---

