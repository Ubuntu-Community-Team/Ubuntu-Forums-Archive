---
title: "Grub cant find windows."
date: 2013-07-18
forum: New to Ubuntu
---

### Post by akshay.sulakhe on 2013-07-18
Hello guys, 
                 I hope you are doing fine today. I ordered a second SSD so i can install windows on it and on my 2nd ssd i can install ubuntu. Both my ssds are 120gb, and while i should have disconnected my ssd, so it doesnt screw up my windows. But i made a mistake and didnt unplug that ssd. By mistake i formatted my ubuntu ssd and windows managed to somehow screw the bootloader. Now when i did a fresh install of ubuntu and even if i give a update-grub i cannot see windows in my list. I can mount the hard disk and see the contents. What shall i do guys? Kindly let me know. Thank you for your time.

---

### Post by oldfred on 2013-07-18
If you can boot Ubuntu run this.
sudo update-grub

If that does not work or you need more help post the link to the BootInfo report. You can run this from your install, an Ubuntu live installer, or download it as a live repair CD.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Boab1993 on 2013-07-18
It is possible that theres just an access problem. 
I had problems on my old windows boot manager trying to find usb drives to boot from, the way i solved it was by installing 'PLOP' 
[http://www.plop.at/en/bootmanager/download.htm]("http://www.plop.at/en/bootmanager/download.html")l
After installing this i was able to boot from all devices.

Hope this helps

---

