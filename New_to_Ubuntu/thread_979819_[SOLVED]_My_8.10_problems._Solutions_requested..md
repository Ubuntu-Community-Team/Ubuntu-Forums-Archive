---
title: "[SOLVED] My 8.10 problems. Solutions requested."
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Statik on 2008-11-12
Hi all,

Yesterday I upgraded my beautifully working 8.04 install on my HP DV2310CA laptop to 8.10. I read over the list of what things were going to be uninstalled and installed and didn't see any troubles, but now I have the following problems, in order of importance to me:

1.    CUPS is not running. I have no access to printers at all. Looking in the System Log Viewer, filtered for CUPS, I see:
```
top cupsd: Unable to open log file "/var/log/cups/error_log" - Permission denied
top cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!
```

I changed the error log to 777, just to see if it helped, but I can't see anything wrong with the conf file. It is setup as:
```
-rw-r--r--   1 root root 2378 2008-11-12 09:43 cupdsd.conf
```

I did edit it to turn on browsing, but that was after I couldn't get anything through System->Administration->Printing or http:localhost:631

2. Very long boot times. Looking in the System Log viewer again, I see the following delays:
```
Nov 12 07:44:01 statik-laptop syslogd 1.5.0#ubuntu6: restart
. . .
Nov 12 07:44:01 statik-laptop kernel: [  97.962787] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
Nov 12 07:44:17 statik-laptop kernel: [ 113.946418] apm: BIOS not found.
Nov 12 07:44:18 statik-laptop kernel: [ 115.500046] Clocksource tsc unstable (delta = -82478907 ns)
Nov 12 07:50:39 statik-laptop kernel: [ 496.294208] Bluetooth: Core ver 2.13
Nov 12 07:50:39 statik-laptop kernel: [ 496.295431] NET: Registered protoval family 31
. . .
Nov 12 07:51:02 statik-laptop pulseadudio[6232]: alsa-util.c Cannot find fallback mixer control "Mic"
Nov 12 07:53:39 statik-laptop kernel: [ 676.284049] ACPI: EC: missing confirmations, switch off interrupt mode.
```

Any assistance would be appreciated. I don't want to reinstall, although my home partition is separate if that becomes an option.

Statik

---

### Post by superprash2003 on 2008-11-12
try resetting the permissions of the cupsd.conf file.. something must have overwritten permissions.. allow your username to read it..

---

### Post by Statik on 2008-11-12
Reset them to what?

Statik

---

### Post by eolson on 2008-11-12
Did you do an upgrade or a fresh install?   Not that it will help much now,  but I've found upgrades to be troublesome, even on a desktop.

---

### Post by Statik on 2008-11-12
It was an upgrade . . . I'm starting to consider doing an install tho. 

The cups issue seems to have been that it wasn't starting cups as root. Still looking into it.

Statik

---

### Post by markjensen on 2008-11-12
During the upgrade (I did my upgrade from within Ubuntu through the update manager, and it went successfully for me), it should have prompted you when it hit your cups config file.  It did for me on grub, samba and one other, I think.

You had choices to keep the original, use the new, or view the differences.  Do you remember what you did?  I think that this may be part of why your cups no longer runs.   Do you have a backup of your file/config?   If so, remove the current config file and restart cups, it should re-create a default file.  You can then re-set it up the way you want.

I think that **this** is one area that Ubuntu needs work on.   I have been a 100% Linux user for over 5 years now (most of that time on Red Hat and Fedora), but these difference reviews were a bit intimidating for me, and some sensible migration ought to be done for the user (perhaps keeping the original and the incoming default as reference files for troubleshooting).

Best of luck!

---

### Post by superprash2003 on 2008-11-13
change permissions of that file to your current username

---

### Post by Statik on 2008-11-19
Well, reinstalled and works great!

Marking solved.

Statik

---

