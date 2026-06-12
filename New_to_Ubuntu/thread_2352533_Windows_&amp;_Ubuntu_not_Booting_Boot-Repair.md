---
title: "Windows &amp; Ubuntu not Booting Boot-Repair"
date: 2017-02-13
forum: New to Ubuntu
---

### Post by anshul.sable009 on 2017-02-13
@oldfred

I am new to Ubuntu. I installed it along side Windows 8. After installing it, I was not able to access Windows 8. So, I followed one of your methods on other thread. I tried to do Boot Repair. Its report is - paste.ubuntu.com/23924936 and 23924987. But that was not helpful. Thereafter I installed Windows 7 through my disk and upgraded to windows 10. I have no access to either Ubuntu or earlier Windows 8. I have to access Ubuntu. What should i do?

---

### Post by oldfred on 2017-02-13
Moved to your own thread to avoid confusion with original poster.

Is this your thread?
[https://paste.ubuntu.com/23924936/](https://paste.ubuntu.com/23924936/)

Looks like an old BIOS with XP that you have upgraded.
Windows has to have a primary partition to boot from which is your sda1 that has both the old XP boot files and newer Windows bootmgr & BCD files.l
Usually better to install Windows in primary partitions.
With Windows 8 or 10 you must make sure fast start up or always on hibernation is off.

Boot-Repair says it reinstalled grub ok.
Does it now boot Ubuntu?
Is system set to AHCI mode in BIOS?

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

