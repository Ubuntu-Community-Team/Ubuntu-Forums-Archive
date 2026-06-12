---
title: "Error: BrokenCount &gt; 0"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by SuzanErven on 2013-04-29
Hi guys,  Ubuntu software center says: "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?" But when I click repair, it gives another error: "Package operation failed"  By clicking on a stop-board icon on the top of my screen I found out the error message is: "Error:  BrokenCount > 0"  I tried apt-get -f install but it says "E: Sub-process /usr/bin/dpkg returned an error code (1)"  I'm sure you guys need more to go on, so just ask me if you need more information :)  Thanks,  Suzan

---

### Post by davidbaumann on 2013-04-29
Give us the full log of apf-get -f install please.

---

### Post by SuzanErven on 2013-04-29
apt-get -f install returns the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.
4 not fully installed or removed.
Need to get 0 B/3,941 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource remporarily unavailable
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:i386
(Reading database ...
dpkg: warning: files list file for package 'ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 205511 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.3 (using .../libc6_2.15-0ubuntu10.4_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb (--unpack):
subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by davidbaumann on 2013-04-29
Bitte schliesse das Softwarecenter, während du apt-get -f install ausführst. Auch ein Neustart könnte Hilfe bringen.

---

### Post by SuzanErven on 2013-04-29
Yeah, I just happen to understand that, but next time please just reply in english, since it's the most common language, and not everyone understands German, kay? Thanks anyway :3

---

### Post by SuzanErven on 2013-04-29
Okay, so I installed the "suggested package": glibc-doc with apt-get install.
it worked out fine, and part of the error disappeared. Now I tried installing ttf-mscorefonts-installer with apt-get install, then this showed up in my terminal:
[ATTACH=CONFIG]241950[/ATTACH]
seems alright, but I can't click on okay, so I'm kinda stuck here. I now remember canceling this is what probably caused my problems in the first place.

Any help on this would be very welcome!

---

### Post by howefield on 2013-04-29
Use the tab key to highlight the OK button and enter to proceed.

---

### Post by SuzanErven on 2013-04-29
Thanks :3 No more errors, setting as solved

EDIT: Okay I can't set it as solved. "Thread tools" only has the options: "Show printable version"; "Email this page"; and "Subscribe to this thread". wth? (I feel really stupid right now)

---

### Post by howefield on 2013-04-29
> **SuzanErven said:**
> EDIT: Okay I can't set it as solved. "Thread tools" only has the options: "Show printable version"; "Email this page"; and "Subscribe to this thread". wth? (I feel really stupid right now)

Don't feel stupid, the forum upgrade is outstanding a plugin to allow marking threads as solved, however there is a "workaround"..

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)

---

### Post by davidbaumann on 2013-04-29
Oops, I'm jumping between .de and .org forums :)

---

