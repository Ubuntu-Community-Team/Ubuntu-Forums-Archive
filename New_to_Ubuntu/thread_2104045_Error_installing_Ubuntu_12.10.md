---
title: "Error installing Ubuntu 12.10"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by hellomeme869 on 2013-01-11
I'm getting this error near the end of the install with wubi. 
> >>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {804ccd93-a900-11e0-bc4a-b5a06c381185} device partition=Y:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
01-11 20:48 DEBUG  TaskList: # Cancelling tasklist
01-11 20:48 DEBUG  TaskList: New task modify_bcd
01-11 20:48 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {804ccd93-a900-11e0-bc4a-b5a06c381185} device partition=Y:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {804ccd93-a900-11e0-bc4a-b5a06c381185} device partition=Y:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
01-11 20:48 DEBUG  TaskList: New task modify_bcd
01-11 20:48 DEBUG  TaskList: New task modify_bcd
01-11 20:48 DEBUG  TaskList: ## Finished modify_bootloader
01-11 20:48 DEBUG  TaskList: # Finished tasklist


---

### Post by hellomeme869 on 2013-01-11
I originally posted this on the general and i felt that was a bad place for it. But i'm getting an error, at what i think is the end of the install. Here's the bottom of my log file:
(My first time installing a actual new version of Ubuntu)
> >>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {804ccd93-a900-11e0-bc4a-b5a06c381185} device partition=Y:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
01-11 20:48 DEBUG  TaskList: # Cancelling tasklist
01-11 20:48 DEBUG  TaskList: New task modify_bcd
01-11 20:48 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {804ccd93-a900-11e0-bc4a-b5a06c381185} device partition=Y:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {804ccd93-a900-11e0-bc4a-b5a06c381185} device partition=Y:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
01-11 20:48 DEBUG  TaskList: New task modify_bcd
01-11 20:48 DEBUG  TaskList: New task modify_bcd
01-11 20:48 DEBUG  TaskList: ## Finished modify_bootloader
01-11 20:48 DEBUG  TaskList: # Finished tasklist

---

### Post by tlhIngan on 2013-01-11
Try the alternate installer or try installing from a live CD.
It looks like wubi is having issues with your windows boot manager.

---

### Post by cariboo on 2013-01-11
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by hellomeme869 on 2013-01-11
Ok sorry, kinda didn't know exactly where to post this. New to these forums

---

### Post by hellomeme869 on 2013-01-11
I'm sorta blind, I've never seen an "alternate installer". I've used the wubi of the iso and that just forces me into the os off the cd. when i got to install it, it doesn't recognize  my partition.

---

### Post by ibjsb4 on 2013-01-11
If your running "dynamic disk", that would be the problem.

[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

---

