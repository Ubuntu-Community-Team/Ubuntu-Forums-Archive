---
title: "Metalink error"
date: 2015-02-21
forum: New to Ubuntu
---

### Post by jose63 on 2015-02-21
I am installing Ubuntu 14.04 on Windows 8.1 using Wubi for dual boot, failed almost at the end with an numerous error from log: ERROR  CommonBackend: The md5 of the metalink does match

Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
Errors: 1
>>stdout=
02-21 11:34 DEBUG  WindowsBackend: command >>C:\Users\Jose\AppData\Local\Temp\pyl855A.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
02-21 11:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
02-21 11:34 DEBUG  TaskList: ### Finished check_iso
02-21 11:34 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
02-21 11:34 DEBUG  TaskList: # Cancelling tasklist
02-21 11:34 DEBUG  TaskList: # Finished tasklist
02-21 11:34 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'

---

### Post by Mark Phelps on 2015-02-21
Windows 8.1 preinstalled machine come preconfigured to use UEFI -- and WUBI doesn't work with UEFI.  WUBI support was dropped back with 12.04.  You should not be using it now.

---

### Post by hakuna_matata on 2015-02-21
> **jose63 said:**
> The md5 of the metalink does match
IMHO it is [bug 1367071]("https://bugs.launchpad.net/wubi/+bug/1367071"). Same issue for 14.04.2. A workaround is [here]("http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html").

Note: In general, Wubi is not recommended. If you use Windows 8.1 in UEFI mode, the linked workaround above is not enough. I patched several Wubi versions also for UEFI and moved these versions to [a dropbox folder]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0") (wubi14041.exe for 14.04.1 and wubi14042.exe for 14.04.2).  

Maybe, you can use these versions to patch your own Wubi.

---

### Post by nerdtron on 2015-02-22
..outdated reply..

---

### Post by jose63 on 2015-02-22
Thank you for the information, I thought I am getting nuts looking for a cure!

---

