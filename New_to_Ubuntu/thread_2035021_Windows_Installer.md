---
title: "Windows Installer"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by 55355g on 2012-07-29
The site offers a "Windows Installer" and the screenshots appear to show a dual boot system after the install.  

Will the installer give me the option to install the operating system to a virtual drive?  

I have two physical drives and quite a few virtual drives.  One or more are probably empty and I could reformat one to a linux drive if necessary.  I'd rather install ubuntu on a virtual drive but it isn't clear from the screenshots if that is an option.

Thanks, Mike

---

### Post by Lyfang on 2012-07-29
I suggest to install Wubi on one of your hard drives. Wubi is easy to uninstall.

See also: [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=2035021")

---

### Post by Cheesemill on 2012-07-29
WUBI installs a full version of Ubuntu, but instead of a traditional dual-boot that uses it's own partition it gets installed to a virtual filesystem which lives on one of your Windows drives.

This virtual filesystem is self-contained in a file called root.disk which by default lives in the C:\ubuntu\disks folder unless you specify a different location during the installation.

---

### Post by 55355g on 2012-07-29
Thank you for your prompt reply.  I take your suggestion to mean that I want to move the installer (wubi.exe) to the drive where I want the program installed.  I have done so and have begun the execution of the installer routine.  At my connect speeds it looks like about 5 hours to install.  

Thanks again for your suggestion.  I tether through a cell phone and have purchased two programs to do this (Tether and EasyTether).  Neither has a linux version.  Anyone have any ideas???  I guess I need to post that querry on another board in the forum.....

Mike

---

### Post by Cheesemill on 2012-07-29
You don't have to run the installer from the location that you wish to install to, you can select the installation drive directly from the installer (see attached screenshot), the root disk file will be created in the \ubuntu\disks\ folder on the drive that you select.

If you want you can [download]("http://releases.ubuntu.com/precise/") the Desktop .iso file manually either from your PC or another computer and place it in the same location as wubi.exe
The WUBI installer will then use this .iso file instead of downloading the file itself.
For more information you should check out this page:
[https://wiki.ubuntu.com/WubiGuide/](https://wiki.ubuntu.com/WubiGuide/)


As for tethering, every mobile phone that I have used with Ubuntu has connected automatically, no need to purchase or download any specialized tethering software.

---

