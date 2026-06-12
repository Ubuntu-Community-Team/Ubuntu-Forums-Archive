---
title: "Bitdefender &quot;Engines not loaded&quot;"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by jmgmayo on 2013-11-14
Hi, 

i just installed Bitdefender for Unices but when i go to the GUI in the Version option appears "Engines Not Loaded". I just review the next post with the solution but i not possible to run like root. I am using sudo but always apperas the next message. I have installed ubuntu 13.10

[http://ubuntuforums.org/showthread.php?t=1971927](http://ubuntuforums.org/showthread.php?t=1971927)

[SIZE=1]*BitDefender Antivirus Scanner for Unices v7.90123 Linux-amd64*
[I][U]Copyright (C) 1996-2009 BitDefender. All rights reserved.
This program is licensed for home or personal use only.
Usage in an office or production environment represents
a violation of the license terms

Error: You need superuser privileges in order to perform an update[/U][/I][/SIZE]


Any help?

Regards.

---

### Post by monkeybrain20122 on 2013-11-14
It has no use. You don't need an AV in Linux.

---

### Post by sammiev on 2013-11-14
> **jmgmayo said:**
> Hi, 

i just installed Bitdefender for Unices but when i go to the GUI in the Version option appears "Engines Not Loaded". I just review the next post with the solution but i not possible to run like root. I am using sudo but always apperas the next message. I have installed ubuntu 13.10

[http://ubuntuforums.org/showthread.php?t=1971927](http://ubuntuforums.org/showthread.php?t=1971927)

[SIZE=1]*BitDefender Antivirus Scanner for Unices v7.90123 Linux-amd64*
[I][U]Copyright (C) 1996-2009 BitDefender. All rights reserved.
This program is licensed for home or personal use only.
Usage in an office or production environment represents
a violation of the license terms

Error: You need superuser privileges in order to perform an update[/U][/I][/SIZE]


Any help?

Regards.


Must be run in root.

```
cat /opt/BitDefender-scanner/var/lib/scan/versions.dat.* |awk '/bdcore.so.linux/{print $3}'|while read bdcore_so;do touch /opt/BitDefender-scanner/var/lib/scan/$bdcore_so;bdscan --update;ln -s /opt/BitDefender-scanner/var/lib/scan/$bdcore_so /opt/BitDefender-scanner/var/lib/scan/bdcore.so;done

rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so
ln -s /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so
```

---

### Post by jmgmayo on 2013-11-15
Thanks. The problem is that i need to execute as a root user but in ubuntu i think there is not activated root user. I am trying to execute using "sudo" command but it doesn't run. 

It is possible to activate the root user or it could be better using oher user. 

I need the bitdefender to scan windows system.

---

### Post by Mark Phelps on 2013-11-15
> but in ubuntu i think there is not activated root user

The root user is installed by default in Ubuntu.

What happens when you try the commands indicated in the post?

---

### Post by jmgmayo on 2013-11-17
The next message is displayed.I use the same user (using sudo command) to install Bitdefender.

Regards.

[SIZE=1]*BitDefender Antivirus Scanner for Unices v7.90123 Linux-amd64*
[I][U]Copyright (C) 1996-2009 BitDefender. All rights reserved.
This program is licensed for home or personal use only.
Usage in an office or production environment represents
a violation of the license terms

Error: You need superuser privileges in order to perform an update[/U][/I][/SIZE]

---

### Post by sammiev on 2013-11-17
> **jmgmayo said:**
> The next message is displayed.I use the same user (using sudo command) to install Bitdefender.

Regards.

[SIZE=1]*BitDefender Antivirus Scanner for Unices v7.90123 Linux-amd64*
[I][U]Copyright (C) 1996-2009 BitDefender. All rights reserved.
This program is licensed for home or personal use only.
Usage in an office or production environment represents
a violation of the license terms

Error: You need superuser privileges in order to perform an update[/U][/I][/SIZE]

This is what I use to get me into root at the ternmail screen.

```
sudo -i
```

---

### Post by jmgmayo on 2013-11-18
Thanks. 

It is true that the system display udated several files but at the end BitDEfender is still showing the message "Engines not loaded". I am trying to execute other time teh first comand but teh suystem display "no update available". Any idea?

Regards.

---

### Post by sammiev on 2013-11-18
I had to run the commands after a fresh boot and before I had any errors. I will be installing it later today as I did a fresh install.

---

### Post by sammiev on 2013-11-18
Just installed Bitdefender and I had the same problem as before.
Went into terminal and then to root.
Ran the 3 lines of code and updated.
Ran a scan without anymore errors.

---

### Post by jmgmayo on 2013-11-18
I just executed  the first line 
[SIZE=1]
cat /opt/BitDefender-scanner/var/lib/scan/versions.dat.* |awk '/bdcore.so.linux/{print $3}'|while read bdcore_so;do touch /opt/BitDefender-scanner/var/lib/scan/$bdcore_so;bdscan --update;ln -s /opt/BitDefender-scanner/var/lib/scan/$bdcore_so /opt/BitDefender-scanner/var/lib/scan/bdcore.so;done[/SIZE]

the system updates files but shows the error that the simbolic link «/opt/BitDefender-scanner/var/lib/scan/bdcore.so» exit.

I run the other two lines but the filed version still show "Engines not loaded". Any help? do I need to restart the system?

Regards.

---

### Post by sammiev on 2013-11-18
Reboot your computer, run the 3 lines in root and update. Then try a scan, the engine should load. :)

---

### Post by computerstudies67 on 2013-12-20
Bitdefender engine not loaded in ubuntu 13.10........i don't know whay and what is solved it.

---

### Post by oldos2er on 2013-12-20
Try ```
sudo rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so

sudo ln -s /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so
``` Gleaned from [http://forum.bitdefender.com/index.php?showtopic=30005](http://forum.bitdefender.com/index.php?showtopic=30005)

---

