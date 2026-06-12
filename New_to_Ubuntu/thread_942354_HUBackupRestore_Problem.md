---
title: "HUBackup/Restore Problem"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by germanix on 2008-10-09
I downloaded the application HUBackup (Home User Back-up) via Synaptic Package Manager. I want to back-up my "Home File" to a USB stick. This application has 2 parts. The first is the actual back-up and the second the "Restore". Once installed you can access the application over System-Admin.
The installation went well. I opened the Back-up Gui and backed-up the home file. I then checked to make sure that the back-up is on the USB stick. It shows 2 files, a master archive and a master catalog file, both shown as .dar files. I now have two problems:
When I try to open any of these files to check the contents, an error message appears: file cannot be opened as there are no application installed for this file type! 
More importantly though when I try to start/open the HURestore application nothing happens, no window opens? So it seems to me that I now have a back-up but cannot restore it when needed.
I de-installed the application and made a new install, I also tried a new install over the add/remove function but all have the same results.
Can anyone put some light on this matter?

---

### Post by Nano Geek on 2008-10-09
Type the following into the terminal and tell me what it says.```
sudo simple-restore-gnome 
```

---

### Post by cliffm on 2008-11-28
Help! All my files are here. Just upgraded to Ubuntu 8.10
I have followed several answer to this problem and can not get any of them to work.
What am I doing wrong? The HUBackup file is 518.7MB, and was saved to a CD. These are some of my attempts to restore and there responses.


~$ dar -l /media/sdb1/backup/cliffm-master-archive
/media/sdb1/backup/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]

:~$ sudo dar -x /cdrom0/backup/cliffm-master-archive -R /home/cliffm -wa -v
[sudo] password for cliffm: 
/cdrom0/backup/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]

m:~$ dar -x.hubackup-data/cliffm-master-archive -R TARGET_DIR 
File ownership will not be restored as dar is not run as root. to avoid this message use -O option [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: File ownership will not be restored as dar is not run as root. to avoid this message use -O option
cliffm@cliffm:~$ sudo dar -x.hubackup-data/cliffm-master-archive -R TARGET_DIR 
[sudo] password for cliffm: 
.hubackup-data/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: .hubackup-data/cliffm-master-archive.1.dar is required for further operation, please provide the file.

---

### Post by TDFlanders on 2009-01-23
Brilliant guys, I lost legal documents. I cannot believe this package was not removed after two years of not working whatsoever. This is a package in MAIN people!!!

Anyway, I verified the integrity of the package in the same hubackup gui as I created it in, and hubackup claim it was fine. I have since reformatted and can no longer restore.

'root# simple-restore-gnome' does not work. 

Any ideas? Please!

It is a segmentation fault, I marked my bug (#320421) as a duplicate of the original one (#64594). I have attached the valgrind and strace.

I saw that Sivan Greenberg was assigned to it and have contacted him.

---

### Post by TDFlanders on 2009-01-26
Sorry about the late reply. I have been a busy little bee. Anyway, I retrieved my data through the dar (-x) command, but the hurestore problem persists. Thanks for helping me out.

---

