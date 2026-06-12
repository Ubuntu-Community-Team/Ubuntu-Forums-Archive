---
title: "Can't boot 14.04.2 from DVD"
date: 2015-06-30
forum: New to Ubuntu
---

### Post by kyle50 on 2015-06-30
So, first let me say this is my first time trying to use any linux distro. I dug around my compuer's bios and set "secure boot" to disabled, as well as adding boot from the disc drive to the boot options list as second priority. I restarted the machine, and a screen asking whether I intended to boot from the DVD (ubuntu) or SSD (Windows 8.1) and I selected ubuntu. This is where things went wrong, and I recieved an error screen containing the following:


***Windows Boot Manager***

*Windows failed to start. A recent hardware or software change might be the cause.*

*File: \ubuntu\winboot\wubildr.mbr*

*Status: 0xc000007b*

*Info: The application or operating system couldn't be loaded because a required file is missing or contains errors.*






Anyway, I checked the contents of the DVD to make sure the iso formatted correctly, and to the best of my knowledge the files are fine; the Ubuntu installer bit that can be opened within Windows works fine.


As a side note, I would have already tried to burn the disc again and see if that fixes the problem, but I cannot get my computer to erase the disc (a DVD RW disc) for the life of me, and would rather not have to use another disc unless absolutely necessary.

---

### Post by oldfred on 2015-06-30
Wubi is not supported anymore. 
You do not start an Ubuntu install from inside Windows, but by rebooting and choosing to boot from DVD or flash drive. I now prefer flash drives.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Be sure to do a fresh backup of Windows, and make a Windows repairCD or flash drive. You should have been prompted to do that when you first booted Windows, also.

Use Windows own disk tools to shrink the NTFS partition and reboot immediately into Windows to let it run its own repairs, chkdsk on it new size.


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support) 
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by kyle50 on 2015-06-30
As far as I can tell, I am not using the "WUBI" you are referring to. I am "rebooting and choosing to boot from DVD". I am able to boot windows fine. Any other suggestions?

---

### Post by oldfred on 2015-06-30
This is wubi.

[I]File: \ubuntu\winboot\wubildr.mbr

Perhaps you installed it before and now your Windows does not like it. Then you may need to use a Windows repair CD or flash drive to repair BCD. That cannot be done from Linux.
[/I]

---

