---
title: "Fixed OpenOffice General input/output error on NFS share"
date: 2007-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by robert114 on 2007-01-05
Hi I've suffered from a rare error with OpenOffice2.1 in combination with NFS! Whenever i saved a file to a NFS share I got the General input/output error from OpenOffice, saving to the local disk did work perfectly
Whenever I opened a file from a NFS share OpenOffice opened it in read only mode!

This problem did occur after I've installed and removed the NFS kernel server on the client side and I've tried to configure file sharing with the KDE applet. (After this I uninstalled the NFS kernel server ).

The next day I discovered that my machine wasn't able to save to the NFS share and opened all the documents read only!

**My dirty solution**
After Googling the net for a solution the only thing I found was disabling the locking function of OpenOffice. Below I've described how you can do this:

1. Open the soffice file with your editor (I used nano)
```
nano /etc/openoffice.org-2.1/program/soffice
```
2. search for this line: SAL_ENABLE_FILE_LOCKING=1 (line 43) 
3. Comment the SAL_ENABLE_FILE_LOCKING=1 and export SAL_ENABLE_FILE_LOCKING lines out by placing a '#' in front of it.
So it looks like this:
```
# file locking now enabled by default
#SAL_ENABLE_FILE_LOCKING=1
#export SAL_ENABLE_FILE_LOCKING
```
4. Save and close the file and restart OpenOffice!

Info about my client system:
Ubuntu Edgy (32 bit)
OpenOffice 2.1 ( unofficial Alient version)

My source of information:
[http://lists.freebsd.org/pipermail/freebsd-openoffice/2006-July/002525.html]("http://lists.freebsd.org/pipermail/freebsd-openoffice/2006-July/002525.html")

Please don't hazatate to ask questions I'm not an expert what Ubunt NFS and OpenOffice concerned but maybe I can help.

If you have a better solution or have used mine please leave a message :) 

chears Robert

---

### Post by robert114 on 2007-01-05
Hi I've suffered from a rare error with OpenOffice2.1 in combination with NFS! Whenever i saved a file to a NFS share I got the General input/output error from OpenOffice, saving to the local disk did work perfectly
Whenever I opened a file from a NFS share OpenOffice opened it in read only mode!

This problem did occur after I've installed and removed the NFS kernel server on the client side and I've tried to configure file sharing with the KDE applet. (After this I uninstalled the NFS kernel server ).

The next day I discovered that my machine wasn't able to save to the NFS share and opened all the documents read only!

**My dirty solution**
After Googling the net for a solution the only thing I found was disabling the locking function of OpenOffice. Below I've described how you can do this:

1. Open the soffice file with your editor (I used nano)
```
nano /etc/openoffice.org-2.1/program/soffice
```
2. search for this line: SAL_ENABLE_FILE_LOCKING=1 (line 43) 
3. Comment the SAL_ENABLE_FILE_LOCKING=1 and export SAL_ENABLE_FILE_LOCKING lines out by placing a '#' in front of it.
So it looks like this:
```
# file locking now enabled by default
#SAL_ENABLE_FILE_LOCKING=1
#export SAL_ENABLE_FILE_LOCKING
```
4. Save and close the file and restart OpenOffice!

Info about my client system:
Ubuntu Edgy (32 bit)
OpenOffice 2.1 ( unofficial Alient version)

My source of information:
[http://lists.freebsd.org/pipermail/freebsd-openoffice/2006-July/002525.html]("http://lists.freebsd.org/pipermail/freebsd-openoffice/2006-July/002525.html")

Please don't hazatate to ask questions I'm not an expert what Ubunt NFS and OpenOffice concerned but maybe I can help.

If you have a better solution or have used mine please leave a message :) 

chears Robert

---

### Post by pjkundert on 2007-01-15
Try installing nfs-common, instead...

The problem is that file locking over NFS requires that 'statd' (actually /sbin/rpc.statd) be running; the nfs-common package arranges for this to be done.

---

### Post by robert114 on 2007-01-15
Well I allready had the nfs-common package but thanks for your reply
maybe it helps somebody else out :KS

---

### Post by cikson on 2007-01-27
I have the same problem and I tried all things above but still can't open files :( 
Dose anyone have suggestions?

Info about my system:
Ubuntu Edgy (AMD64)
OpenOffice.org 2.0.4 

Please help.

---

### Post by Dubbayoo on 2007-02-18
neither solution worked for me either.

---

### Post by mbradlcu on 2007-02-21
Hi, and thanks for the fix,
the only deviation I had was the file you mentioned on my systems was here:
vi /usr/lib/openoffice/program/soffice

a question for the other poster that issue wasn't resolved, are you using nfs to mount /home?

---

### Post by cikson on 2007-02-24
> **mbradlcu said:**
> 
a question for the other poster that issue wasn't resolved, are you using nfs to mount /home?

No

---

### Post by Dubbayoo on 2007-02-27
> **mbradlcu said:**
> Hi, and thanks for the fix,
the only deviation I had was the file you mentioned on my systems was here:
vi /usr/lib/openoffice/program/soffice

a question for the other poster that issue wasn't resolved, are you using nfs to mount /home?

yes, but your solution worked.

---

### Post by dajorad on 2007-03-03
The nfs-common package will already be loaded on the server but it also needs to be loaded onto the client computer that is running openoffice.

I just loaded this package and it solved the problem for me.

---

### Post by gyst on 2007-03-08
Installing nfs-common on the desktop wasn't enough for me.

I switched my old woody NFS server from nfs-user-server to nfs-kernel-server. Rebooted both the server and the desktop. That did fix it.

---

### Post by tansooeng on 2007-11-20
Install the nfs-kernel-server instead of nfs-user-server and with the correct configuration in /etc/exports solved the problem even without any modification on /usr/lib/openoffice/program/soffice.

I solved this in 3 days.

---

