---
title: "Dual boot installation with windows 8 on lenovo y500"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by gauravp on 2013-05-16
Hello,


I recently bought a Lenovo Ideapad Y500 in which i tried to install ubuntu but was unable to do so.
First I made a 100GB partition in disk management of Windows 8 and the I turned the Secure Boot 'OFF'
, and changed the boot mode from UEFI to 'Legacy mode' and kept the boot first as 'UEFI first' and 
then I booted up the Ubuntu 12.04.2-amd64 LiveCd and 


1. Got and unusual start up window in ubuntu.(photo - [http://postimg.org/image/7x3glg6ln/](http://postimg.org/image/7x3glg6ln/)) I by mistake selected Install ubuntu option.The computer stopped,
   I manually shut it down.Later i rebooted the CD and this time i got the same window and then I selected
   Try ubuntu and then installed Ubuntu and after installation i restarted without doing boot-repair.


2. I again rebooted the CD and this time I selectes the option of 'remove existing ubuntu installation and 
   resintall' (1st option), it installed fine. After installation did the recommended boot-repair but during shutdown
   I bymistake selected 'suspend' (there are posts where after installation of ubuntu in this model,one can't 
   suspend the laptop unless some drivers are resintalled). Since, I had no option I manually shut it down.


3. On boot-up a screen saying boot-failure.(photo - [http://postimg.org/image/46032w3tr/](http://postimg.org/image/46032w3tr/)) On going in the boot-options.There was two options of 'Windows Boot Manager'
   and two options of 'Ubuntu'. None of them worked, it said it was against the system secrity poliicy.


4. I used Lenovo's one key recovery system which took me back to initial factory settings of the laptop. Now if i
   go in the boot options I see a two 'Windows Boot Manager option' and a 'Ubuntu' option.I formatted the allocated 
   100 GB usug disk management but it still showed the ubuntu entry and two windows boot manager option instead of the
   usual one option.


5. After all this I again booted up the Ubuntu and installed it in the 100gb partition (Something else option).
   Ran boot-repair and on restarting it again showed boot-failure as in the Step3 , so i again recovered my PC.
   
What should is do now?
How shall I install Ubuntu inn this system?
Should I try going the wubi way for 32bit ubuntu in my 64bit laptop?


Regards,
Gaurav

---

### Post by fantab on 2013-05-16
[QUOTE=gauravp]I recently bought a Lenovo Ideapad Y500 in which i tried to install ubuntu but was unable to do so.
First I made a 100GB partition in disk management of Windows 8 and the I turned the Secure Boot 'OFF'
, and changed the boot mode from UEFI to 'Legacy mode' and kept the boot first as 'UEFI first' and 
then I booted up the Ubuntu 12.04.2-amd64 LiveCd and[/QUOTE]

Both OS HAVE to be in UEFI or both HAVE to be in 'Legacy'.
Return boot mode to UEFI. Run Windows Recovery, if you have to after resetting UEFI and Try again installing Ubuntu.
If you have a pre-installed SSD then check if you have 'Intel SRT" enabled. You have to disable it.

If after installation of Ubuntu there are any Boot issues use **[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")**.

EDIT: to fix those efi boot entries you need **efibootmgr**: [http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

---

### Post by oldfred on 2013-05-16
+1 on fantab's suggestions.

You cannot use wubi with gpt partitioned drives. All systems booting with UEFI use gpt partitioning so they cannot use wubi. And with gpt there is no issue on primary partitions, so adding partitions is not an issue.

Other Lenovo threads
       Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by gauravp on 2013-05-17
As suggested above, I recovered my initial windows back and then I made a bootable USB of Ubuntu 13.04 and changed the grub entry of gfx="1920x1080" and the "quiet splash" to "nomodeset=1".I was successful in installing(using the install Ubuntu option in the grub menu). The PC restarted and I again booted it with the USB and went to "try Ubuntu without installing" option, it just got stuck on a black screen. <br/> I can access windows by selecting the windows boot manger in boot options but If I chose the Ubuntu option it shows the grub menu but on selecting the "Ubuntu" option in the grub I get the similar black screen with a command "kvm disabled by bios". I have no clue what to do now.Is it the graphic drivers which are the cause of this black screen.I am pretty frustrated after trying so many things, I am totally disappointed by this uefi and windows 8. Please help guys...

---

### Post by fantab on 2013-05-17
You have to add "nomodeset" option again to boot Ubuntu from USB... [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

After booting with Ubuntu USB install BOOT-REPAIR and run "recommended repairs", that should fix your boot issues. if there are any further problems post the link generated by "BootInfo Summary" here.

Good Luck...

---

### Post by gauravp on 2013-05-17
I changed the quietsplash to nomodeset=1 by using the e option in the grub menu, it seems to boot up but now I get a terminal like interface rather than the gui being shown...please help...

---

### Post by fantab on 2013-05-17
That is because you've removed "quiet splash". It is not an issue. However, if you want to get back the GUI you have add it back, so that with 'nomodeset' the entry looks like this: **"quiet splash nomodeset"**. When you add 'nomodeset' you are telling the linux kernel to load any specific graphic drivers and instead use 'open-source' basic driver. Now this opensource driver is very basic and does not offer any 2D or 3D accleration. 

After you've installed Ubuntu and reboot, during reboot from Hard Disk you have to add 'nomodeset' again to the kernel line. Then you have to install "Additional Driver" for your Graphics Card. You can install this from "System Settings -> Additional Drivers". 

By the way, What Graphics do you have? I think it has 'NVIDIA GeForce', confirm with exact model number. You can also type the exact name and number in the forum 'Search' and search for the card to learn more.

---

### Post by gauravp on 2013-05-18
On changing from nomodeset to quiet splash nomodeset,  initially it shows the purple sceen with ubuntu logo (usual booting).... After few seconds again the terminal comes again...what to do?

---

### Post by fantab on 2013-05-18
> **gauravp said:**
> On changing from nomodeset to quiet splash nomodeset,  initially it shows the purple sceen with ubuntu logo (usual booting).... After few seconds again the terminal comes again...what to do?

What does it say?

---

### Post by gauravp on 2013-05-18
It says welcome to ubuntu <br/> for.documentation go to www.ubuntu.com/...<br/> [email]ubuntu@ubuntu$-.,...it[/email] is same as  the terminal like interface which I get on nomodeset setting....

---

### Post by gauravp on 2013-05-18
[http://www.youtube.com/watch?v=PhZeGAcRfa0](http://www.youtube.com/watch?v=PhZeGAcRfa0)  here is what happens

---

### Post by gauravp on 2013-05-18
[http://www.youtube.com/watch?v=PhZeGAcRfa0](http://www.youtube.com/watch?v=PhZeGAcRfa0)  edit:sorry fr spamming

---

### Post by fantab on 2013-05-18
Simple solution: reinstall Ubuntu. Remember to use 'nomodeset' correctly. Read, "**[SIZE=2]How to enable kernel options on the livecd (before install)[/SIZE]**" @ [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132). It is very simple. Don't manually add anything to the kernel line.

---

