---
title: "&quot;Permission denied&quot; when I try to install ubuntu"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by max85 on 2015-02-16
I wanted to change my laptop from window 7 to ubuntu 14.04
I downloaded the 64-bit file from: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
I have 4 GB ram

i ran the "wubi.exe", it download some stuff, progress bar got to 100% and then I got "an error has occurred" "Permission denied". it told me to look at a log file for more information.

this is the bottom of the log file "wubi-14.04-rev286.log":
[HR][/HR]

Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Maxwell\AppData\Local\Temp\pylCAD.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
02-12 13:54 DEBUG  WindowsBackend: command >>C:\Users\Maxwell\AppData\Local\Temp\pylCAD.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
02-12 13:54 DEBUG  Distro:     does not contain casper\filesystem.squashfs
02-12 13:54 DEBUG  TaskList: ### Finished check_iso
02-12 13:54 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
02-12 13:54 DEBUG  TaskList: # Cancelling tasklist
02-12 13:54 DEBUG  TaskList: # Finished tasklist
02-12 13:54 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
[HR][/HR]
Thank you for tolerating my incompetents and hight-littering my ignorants. I think I need to educate my self feather before I'm ready to do things like this. currently I know pretty much when it comes to how they are structured and how to interact with them. I'm going to go away now

thank you

---

### Post by ajgreeny on 2015-02-16
> **max85 said:**
> I wanted to change my laptop from window 7 to ubuntu 14.04
I downloaded the 64-bit file from: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
I have 4 GB ram

i ran the "wubi.exe", it download some stuff, progress bar got to 100% and then I got "an error has occurred" "Permission denied". it told me to look at a log file for more information.
First thing to say is that wubi is not supported any more so it is definitely not a good idea to use it.
It was never intended to be a way to install a full running OS, but more a way to try the OS before a proper installation to partitions.

Secondly, it sounds as if you do not want to use windows any more.  However, installing ubuntu that way would not change you laptop from windows to ubuntu, it would just run ubuntu as a large root-disk file, a virtual OS, but it would still be totally dependent on the windows installation that contained it, and if that was not kept updated and secure you could also loose ubuntu.

So forget wubi; do a real partitioned installation either as a dual boot if you do want to keep windows or as a sole OS which makes life a bit simpler.

Do you know if your laptop uses legacy BIOS or UEFI; that will make a big difference to the way you must proceed.
[UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by mastablasta on 2015-02-16
if you want a dual boot - all you need is a free disk space available. make sure that you have no more than 3 primary partitions occupied. and then you are set to go. just select install next to windows or something like that.

---

### Post by roger_1960 on 2015-02-16
Hi

If you choose to do a full install of just Ubuntu I suggest you download the iso from the ubuntu site, burn it to a cd, dvd or usb thumbdrive to create a bootable medium and then boot it and run the "try it without installing" option to make sure your hardware works OK before wiping out windows.  Once you are sure it works (check that you have an internet connection at least) then install it using the options in the boot menu.  Note also that many windows installations on laptops have a recovery partition on the hard drive (rather than cds or a dvd) and so if you delete windows from your laptop, you may have no way to reinstall it - check you have this covered, after all you have already paid for the windows license!

Roger

---

