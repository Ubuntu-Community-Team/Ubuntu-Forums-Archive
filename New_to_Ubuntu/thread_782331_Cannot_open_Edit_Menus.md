---
title: "Cannot open Edit Menus"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by noorez on 2008-05-04
I tried to open the Edit Menus but the app wouldn't open. I then opened a terminal and tried alacarte but I got this message:

noorez@noorez-laptop:~$ alacarte 
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/noorez/.config/menus/applications.menu'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_alacarte.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/noorez/.config/menus/applications.menu'

Why can't I edit config files in my own home dir ? I don't remember changing permissions at all.

I just reinstalled my system, and I have not done anything differently at all! The last time around I did have access to them. Any help on this?

---

### Post by noorez on 2008-05-06
bump

---

### Post by subzero316 on 2008-05-06
try with sudo command ..also check the premissions...if not right use chown command to change that

---

### Post by noorez on 2008-05-06
Ok, I tried to change the permission, and it has worked. The file was owned by root. Just wondering though why it would have been owned by root? Could some update or application have changed it?

---

### Post by subzero316 on 2008-05-06
> **noorez said:**
> Ok, I tried to change the permission, and it has worked. The file was owned by root. Just wondering though why it would have been owned by root? Could some update or application have changed it?


Cheers...
Yea the updates must have do it..... 
_________________________
(medal on right is 'Thank U':) ') .

---

### Post by SupaSonic on 2008-05-06
All the files in /usr/bin are owned by root. You just have to have the execute permissions. I think sudo chmod +x /usr/bin/alacarte would do the trick

---

### Post by roccivic on 2008-06-26
> **noorez said:**
> Ok, I tried to change the permission, and it has worked. The file was owned by root. Just wondering though why it would have been owned by root? Could some update or application have changed it?

I actually have exactly the same problem: [http://ubuntuforums.org/showthread.php?t=841289](http://ubuntuforums.org/showthread.php?t=841289)

The permissions of what do I have to change?

Thank you.

Rouslan

EDIT: Nevermind, solved

---

