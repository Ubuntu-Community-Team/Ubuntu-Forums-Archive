---
title: "Logs..."
date: 2008-11-03
forum: New to Ubuntu
---

### Post by jasex on 2008-11-03
So recently my root directory was clogged, and it only has 10 gigs, and 5 gigs alone was in /var/logs... stupidly I deleted them, and now I get weird messages from different things...

like this 
E: Directory '/var/log/apt/' missing


How can I fix these... and also any other tips that might help on keeping your root partition clean... i.e. how to cleanse temporary files of firefox or something because it's still like 60%+ filled, and I know I haven't installed that many programs.

---

### Post by cariboo on 2008-11-03
Just recreate the missing directories. Here is a listing from my /var/log directory:

```
ls -l
total 4164
drwxr-xr-x 2 root   root   4096 2008-10-08 17:28 apparmor
drwxr-xr-x 2 root   root   4096 2008-10-31 18:18 apt
-rw-r--r-- 1 root   root   1349 2008-11-03 14:29 aptitude
-rw-r----- 1 syslog adm   30277 2008-11-03 19:29 auth.log
-rw-r----- 1 syslog adm   11070 2008-10-31 19:48 auth.log.0
-rw-r----- 1 root   adm      31 2008-10-31 18:18 boot
-rw-rw-r-- 1 root   utmp    384 2008-10-31 19:51 btmp
drwxr-xr-x 2 root   root   4096 2008-10-31 19:06 ConsoleKit
drwxr-xr-x 2 root   root   4096 2008-11-03 09:29 cups
-rw-r----- 1 syslog adm  120110 2008-11-03 19:15 daemon.log
-rw-r----- 1 syslog adm   37797 2008-10-31 19:48 daemon.log.0
-rw-r----- 1 syslog adm  111778 2008-11-03 19:15 debug
-rw-r----- 1 syslog adm   32387 2008-10-31 19:47 debug.0
drwxr-xr-x 2 root   root   4096 2008-10-24 15:44 dist-upgrade
-rw-r--r-- 1 root   root    674 2008-11-03 19:15 dkms_autoinstaller
-rw-r----- 1 root   adm   39379 2008-11-03 19:14 dmesg
-rw-r----- 1 root   adm   39489 2008-11-03 09:24 dmesg.0
-rw-r----- 1 root   adm   11069 2008-11-02 19:23 dmesg.1.gz
-rw-r----- 1 root   adm   11029 2008-11-02 14:12 dmesg.2.gz
-rw-r----- 1 root   adm   11177 2008-11-02 14:11 dmesg.3.gz
-rw-r----- 1 root   adm   11039 2008-11-02 09:06 dmesg.4.gz
-rw-r----- 1 root   adm  915074 2008-11-03 14:34 dpkg.log
-rw-r--r-- 1 root   root  32064 2008-11-03 14:26 faillog
-rw-r--r-- 1 root   root   2763 2008-10-31 21:05 fontconfig.log
drwxr-xr-x 2 root   root   4096 2008-10-31 18:18 fsck
drwxr-xr-x 2 root   root   4096 2008-11-03 19:15 gdm
drwxr-xr-x 3 root   root   4096 2008-10-31 19:05 installer
-rw-r----- 1 syslog adm  657405 2008-11-03 19:32 kern.log
-rw-r----- 1 syslog adm  189142 2008-10-31 19:48 kern.log.0
-rw-rw-r-- 1 root   utmp 292584 2008-11-03 14:26 lastlog
-rw-r----- 1 syslog adm       0 2008-10-31 18:18 lpr.log
-rw-r----- 1 syslog adm       0 2008-10-31 18:18 mail.err
-rw-r----- 1 syslog adm       0 2008-10-31 18:18 mail.info
-rw-r----- 1 syslog adm       0 2008-10-31 18:18 mail.log
-rw-r----- 1 syslog adm       0 2008-10-31 18:18 mail.warn
-rw-r----- 1 syslog adm  568879 2008-11-03 19:32 messages
-rw-r----- 1 syslog adm  158715 2008-10-31 19:48 messages.0
drwxr-sr-x 2 news   news   4096 2008-10-31 19:06 news
-rw-r--r-- 1 root   root      0 2008-10-31 18:51 pycentral.log
drwxr-x--- 2 root   adm    4096 2008-10-10 07:13 samba
-rw-r----- 1 syslog adm   87060 2008-11-03 19:32 syslog
-rw-r----- 1 syslog adm  320264 2008-11-03 09:29 syslog.0
-rw-r----- 1 syslog adm   48842 2008-11-02 01:48 syslog.1.gz
-rw-r----- 1 syslog adm   77077 2008-11-01 09:06 syslog.2.gz
-rw-r--r-- 1 root   root 411161 2008-11-03 19:14 udev
drwxr-xr-x 2 root   root   4096 2008-11-01 09:12 unattended-upgrades
-rw-r----- 1 syslog adm   38799 2008-11-03 19:29 user.log
-rw-r----- 1 syslog adm    7053 2008-10-31 19:48 user.log.0
-rw-r--r-- 1 root   root      0 2008-11-03 09:29 wpa_supplicant.log
-rw-r--r-- 1 root   root     20 2008-11-02 01:51 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root   root     20 2008-10-31 19:06 wpa_supplicant.log.2.gz
-rw-rw-r-- 1 root   utmp  91776 2008-11-03 19:44 wtmp
-rw-r--r-- 1 root   root    545 2008-10-31 19:00 wvdialconf.log
-rw-r--r-- 1 root   root  15531 2008-11-03 19:15 Xorg.0.log
-rw-r--r-- 1 root   root  15861 2008-11-03 18:29 Xorg.0.log.old
```

All the lines that start with **d** are directories. /var/log/installer also has another directory called **cdebconf**. Make sure all the directories should be owned the same as in the above list.

Jim

---

### Post by jasex on 2008-11-04
could anyone possibly make a script for all that or something... o_o that looks like just a plain old headache to complete manually, and I'm think I might just kick the *buntu and re install

---

### Post by flashgc on 2008-11-04
You might not need to recreate all of that.... just pay attention to the error msgs you get and note what it says is missing. Those you may have to recreate. Others may very well create the log file if it doesn't find one present.

In future, you may prefer to copy /dev/null to the file rather than delete it. /dev/null is a bit bucket and copying it to a file leaves the file attributes intact, leaves the file there, but makes it empty. You may have to fiddle with the command structure (I haven't done it m'self yet) but I've seen reference to this technique for exactly this circumstance.

---

### Post by cariboo on 2008-11-04
How about trying:

```
sudo mkdir -p apparmor apt ConsoleKit cups dist-upgrade dist-upgrade/cdebconf fsck gdm installer news samba unattended-upgrades
```

I mean how hard can it be?

BTW: you have to be in /var/log before running the above commands. :)

Jim

---

### Post by antmenj on 2008-11-04
If you can get your hands on a larger drive you can clone an install to a new drive.;)

---

