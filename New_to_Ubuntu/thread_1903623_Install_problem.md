---
title: "Install problem"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by pamacs on 2012-01-02
Folks-
I am new to Ubuntu. I am attempting to install v11.10 as a Windows app under Vista/SP2. I sucessfully download wubi.exe and launch it. It runs fine but at the end it displays a window informing me there is an error and telling me to look at a log file in my \user\...\appdata\local\temp\ folder. But no log file is there. The folder is empty. I search my C: disk for wubi and still find no log file anywhere. Anyone experience a problem of this nature? Any suggestions/advice would be appreciated. Thanks.
-Gary

---

### Post by bcbc on 2012-01-02
Check the %temp% folder.

The file is wubi-11.10-rev245.log

---

### Post by pamacs on 2012-01-03
Thanks, I found it. Here is the end portion of the log where I first see the word "error." I don't know how to interpret what is wrong. Any help is appreciated.
 
01-02 20:39 ERROR  TaskList: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'
01-02 20:39 DEBUG  TaskList: # Cancelling tasklist
01-02 20:39 DEBUG  TaskList: # Finished tasklist
01-02 20:39 ERROR  root: [Errno 13] Permission denied: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'F:\\wubildr'

 
 
 
-Gary

---

### Post by chipbuster on 2012-01-03
Confirm that the text you have in the error is the same as the text in this bug:
[URL="https://bugs.launchpad.net/wubi/+bug/862003"]
https://bugs.launchpad.net/wubi/+bug/862003[/URL]

If so, it looks like the install actually completed just fine and there's a bug that causes it to return an error. Have you tried actually rebooting your computer and accessing Ubuntu?

---

### Post by pamacs on 2012-01-03
Thanks for the suggestion. The confusing aspect of the error was that I had no F: disk connected and could not understand why it was involved. Anyway I uninstalled Ubuntu, restarted Windows, and began the WUBI install again. Then I noticed that it was installing a 64 bit version. So I uninstalled, restarted, and installed again after figuring out how to force the 32 bit version. Final result, error free install. Now I'm going to give Ubuntu a go....thanks for the replies.
 
-Gary

---

### Post by anewguy on 2012-01-04
And please remember - wubi is meant mainly as a way of taking a "test drive" of ubuntu.  When you get to the point you decide you really want to use ubuntu, you really should either dual-boot (most common until you are SURE you can do everything in ubuntu the way you want to) or a complete installation.

Welcome to ubuntu - hope you like it!

Dave ;)

---

