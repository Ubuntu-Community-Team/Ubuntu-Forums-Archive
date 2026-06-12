---
title: "Grub rescue"
date: 2020-10-16
forum: New to Ubuntu
---

### Post by coilzed on 2020-10-16
Hello guys,

I have 2 SSDs and 1 HDD after repartition I've had grub rescue console when I boot on my ssd with Windows 10(even after reinstalling). Kubuntu on my other one works perfectly. Tried a lot of things from the internet, but couldn't fix it yet. As I know I even don't need grub at all. To boot my windows cause I just can change priority in BIOS. Do someone already encounter situation like this one?

---

### Post by wildmanne39 on 2020-10-16
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by ActionParsnip on 2020-10-16
You will need GRUB to boot Ubuntu. GRUB isn't exclusively for dual boot systems.
Why mess with BIOS settings when GRUB can boot both of your operating systems in a clean and easy way.

---

### Post by oldfred on 2020-10-16
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Grub only boots working Windows. And that also means Windows cannot be hibernated. Windows turns fast start up back on with updates, so you may have to directly boot Windows and turn if off regularly. 
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

