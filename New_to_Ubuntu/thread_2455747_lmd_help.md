---
title: "lmd help"
date: 2020-12-26
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-26
if i put the following script in crontab 

#!/bin/bash
echo xxxx| sudo -S sudo maldet -a /usr/bin  > $HOME/maldetlog

i get the following results 
Linux Malware Detect v1.6.4
            (C) 2002-2019, R-fx Networks <proj@rfxn.com>
            (C) 2019, Ryan MacDonald <ryan@rfxn.com>
This program may be freely redistributed under the terms of the GNU GPL v2

maldet(105268): {scan} signatures loaded: 17188 (14366 MD5 | 2039 HEX | 783 YARA | 0 USER)
maldet(105268): {scan} building file list for /usr/bin, this might take awhile...
maldet(105268): {scan} setting nice scheduler priorities for all operations: cpunice 19 , ionice 6
maldet(105268): {scan} scan returned empty file list; check that path exists and contains files in scope of configuration.
job finished on 12-26-2020 @13:58:03

however if i run the same command in terminal
sudo maldet -a /usr/bin  > $HOME/maldetlog
note i have to put my password in at prompt
i get this result
inux Malware Detect v1.6.4
            (C) 2002-2019, R-fx Networks <proj@rfxn.com>
            (C) 2019, Ryan MacDonald <ryan@rfxn.com>
This program may be freely redistributed under the terms of the GNU GPL v2

maldet(107181): {scan} signatures loaded: 17188 (14366 MD5 | 2039 HEX | 783 YARA | 0 USER)
maldet(107181): {scan} building file list for /usr/bin, this might take awhile...
maldet(107181): {scan} setting nice scheduler priorities for all operations: cpunice 19 , ionice 6
maldet(107181): {scan} file list completed in 0s, found 4 files...
maldet(107181): {scan} found clamav binary at /usr/bin/clamdscan, using clamav scanner engine...
maldet(107181): {scan} scan of /usr/bin (4 files) in progress...
maldet(107181): {scan} clamscan returned an error, check /usr/local/maldetect/logs/clamscan_log for details!

maldet(107181): {scan} scan completed on /usr/bin: files 4, malware hits 0, cleaned hits 0, time 4s
maldet(107181): {scan} scan report saved, to view run: maldet --report 201226-1411.107181
i think problem is that maldet must run as root and the process i have used to run script as root

#!/bin/bash
echo xxxx| sudo -S sudo maldet -a /usr/bin  > $HOME/maldetlog
is not working and ideas
this has been working on most scripts i have used over the years
tks

---

### Post by rburkartjo on 2020-12-26
so if i run in terminal it works but not in crontab

---

### Post by ActionParsnip on 2020-12-26
Use full paths to executables and files

---

### Post by Holger_Gehrke on 2020-12-26
If you want to execute a cron-job with root permissions, don't use sudo inside a user crontab (passwords in scripts are double-plus-ungood, mkay?). Use the root crontab.

Also according to the [readme of maldet at rfxn.com]("https://www.rfxn.com/appdocs/README.maldetect") (search for '.: 10'), it already installs a cron job by dropping a script in /etc/cron.daily/, which should be running as root.

Holger'

---

### Post by rburkartjo on 2020-12-27
here is what i am looking for want to put maldet --scan-all /  in a script had i can add to crontab/tks

---

