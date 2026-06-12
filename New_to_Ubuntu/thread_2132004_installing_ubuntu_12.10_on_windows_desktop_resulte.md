---
title: "installing ubuntu 12.10 on windows desktop resulted in ubuntu freeze before login"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by rtischer8277 on 2013-04-03
I have had a previous Ubuntu version running on my Dell Desktop before. There is plenty of disk space. My problem started when I let the Ubuntu Update Manager install the waiting updates that the nag screen was constantly reminding me about. The update failed and resulted in a frozen screen when booting Ubuntu. Windows 8 still worked fine. Well, almost. I did a clean install of 12.10, but it still froze before the Login screen. I noticed that after the attempted boot, my network connection was clobbered in the Windows boot. I mean really clobbered. Even the ISP couldn't reset it. I have noticed that there are other beginner users who have posted threads about loss of WiFi. I finally switched IP addresses and could connect to the network again. The same thing happened several days later when I again tried to boot up under Ubuntu. Again only by changing the clobbered IP address to a fresh one could I regain connection to the network. My question is, what is the next step? I could erase the failing Ubuntu OS and start over again, but I don't have any reason to believe the results will be any different. BTW, I used the Windows Installer to install Ubuntu 12.10.

---

### Post by gordintoronto on 2013-04-03
I suggest you go into Add/Remove programs and remove Ubuntu. Then use the Windows tools to "shrink" your Windows partition.

Use pendrivelinux to make a bootable flash drive containing Ubuntu. Confirm that you can boot and run from the flash drive. (You will probably need to go into your BIOS settings to do that.) [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

"Back to the C: drive, I right-clicked and selected Properties.  One of the "Properties" is Tools, and one of the Tools is defragmentation. I ran that.

In Windows Control Panel, search for "disk," and one of the items is "Create and format hard disk partitions." I clicked on it, highlighted the C: drive and selected "Action," "All Tasks," "Shrink Volume."

Now install Ubuntu "alongside" Windows.

---

### Post by AndyOpie150 on 2013-04-04
A pretty handy way to boot to floppy disk, CD/DVD drive, USB drive, or hard drive is to install Plop Boot Manager. This eliminates the need to go into the BIOS every time you need to boot from a different drive.

---

