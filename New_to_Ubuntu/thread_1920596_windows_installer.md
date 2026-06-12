---
title: "windows installer"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by mikekolff on 2012-02-05
I just attempted to install ubuntu on  my acer aspire 5253 running windows 7 using the windows installer option but the install failed twice with error message 13. The following is the last part of the install log.

02-05 22:17 DEBUG  WindowsBackend: Copying C:\Users\Karen\AppData\Local\Temp\pyl928E.tmp\winboot -> C:\ubuntu\winboot
02-05 22:17 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-05 22:17 DEBUG  TaskList: # Cancelling tasklist
02-05 22:17 DEBUG  TaskList: # Finished tasklist
02-05 22:17 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'

Any ideas on what went wrong?
Cheers

---

### Post by GPilot on 2012-02-05
> **mikekolff said:**
> I just attempted to install ubuntu on  my acer aspire 5253 running windows 7 using the windows installer option but the install failed twice with error message 13. The following is the last part of the install log.

02-05 22:17 DEBUG  WindowsBackend: Copying C:\Users\Karen\AppData\Local\Temp\pyl928E.tmp\winboot -> C:\ubuntu\winboot
02-05 22:17 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-05 22:17 DEBUG  TaskList: # Cancelling tasklist
02-05 22:17 DEBUG  TaskList: # Finished tasklist
02-05 22:17 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'

Any ideas on what went wrong?
Cheers

First of all: Did you run the wubi (windows installer) with administrator powers? If not, that might be a problem.
Secondly: Try this: Download the appropriate ISO image from [www.ubuntu.com](www.ubuntu.com) and put it together with Wubi (also availible for download on the website) in one folder. Wubi will install from there and not download maybe the wrong file. 
Hope it helps.

---

### Post by mikekolff on 2012-02-06
Thanks heaps:P

---

