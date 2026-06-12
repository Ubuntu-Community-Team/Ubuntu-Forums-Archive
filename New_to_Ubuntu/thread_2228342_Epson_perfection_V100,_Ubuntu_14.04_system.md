---
title: "Epson perfection V100, Ubuntu 14.04 system"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-06-06
I have an Epson perfection V100. 

The scanner used to work with Ubuntu 12.04-32bit LTS DTE. 

I installed 14.04, and now the scanner will not work with the computer. I have downloaded the drivers from the Epson website. Isimple scan used to recongnize the Epson scanner, but now it doesn't.

 I now don't know what to do!

---

### Post by JeQhdMD on 2014-06-06
Before trying more involved solutions, check (via the dash tool) if "Simple Scan" is installed.   If it's not, go to the Ubuntu Software Center, install it, and then open it and try a test scan.

If this doesn't work, let us know, there are other scanner applications (xsane, etc.) that we can try.

---

### Post by bertan2 on 2014-06-07
How are you connecting the scanner to the machine? Is it USB or wired network or wireless network or ... ?

---

### Post by pdc on 2014-06-07
having troubles there paper pusher

what does

> [COLOR="#FF0000"]dpkg -l | grep iscan[/COLOR] give please?

---

### Post by Paper Pusher on 2014-06-22
I apologize for the really late reply. We didn't get the memo that you got back to us. The scanner is connect by a USB to the server computer. The server is a dual core atom machine that is running Ubuntu 14.04.

---

### Post by Paper Pusher on 2014-06-22
Hi pdc, I apologize for the late reply. I got caught up in some other forums and didn't get the memo that your replied. I put in the command you offered and this is what it gave me,

 caregivers@axel-O-E-M:~$ dpkg -l | grep iscan
rc  iscan                                                 2.29.3-1~usb0.1.ltdl7                               i386         simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                            1.28.0-2                                            all          Image Scan! for Linux data files
caregivers@axel-O-E-M:~$

---

### Post by pdc on 2014-06-24
what happens with 

> [COLOR="#FF0000"]iscan[/COLOR]

from a terminal please?

---

### Post by Paper Pusher on 2014-06-24
This is what I get:  

caregivers@axel-O-E-M:~$ iscan
No command 'iscan' found, did you mean:
 Command 'bscan' from package 'bacula-sd-mysql' (main)
 Command 'bscan' from package 'bacula-sd-sqlite3' (main)
 Command 'bscan' from package 'bacula-sd-pgsql' (main)
 Command 'pscan' from package 'pscan' (universe)
 Command 'uscan' from package 'devscripts' (main)
 Command 'scan' from package 'dvb-apps' (universe)
 Command 'scan' from package 'mailutils-mh' (universe)
 Command 'scan' from package 'nmh' (universe)
 Command 'hscan' from package 'ganeti-htools' (universe)
 Command 'qscan' from package 'qpxtool' (universe)
iscan: command not found

---

### Post by pdc on 2014-06-25
so you can run your scanner with the open-source route: SANE and its frontends such as xsane or simple scan;

if you install Epson's iscan software, I understood it ran with the command > iscan .........I don't know why it is not recognised on your system; as you seem to have iscan installed; and the data package

---

