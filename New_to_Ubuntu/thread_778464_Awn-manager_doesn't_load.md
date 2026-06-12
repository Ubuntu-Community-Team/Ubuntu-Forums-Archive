---
title: "Awn-manager doesn't load"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by adnansanni on 2008-05-02
Hi guys, I've install “awn-manager” with Synaptic package manager. But when I click System>Preferences>Awn manager nothing happen.
Any help? I'm using Hardy Heron.

---

### Post by Michael.Godawski on 2008-05-02
What happens if you run ```
awn-manager
``` in terminal?

---

### Post by P4oL1n0 on 2008-05-02
Can you try to open avant with a terminal? so we can see any potential errors...

Just type:
```
awn-manager
```
bye

---

### Post by adnansanni on 2008-05-02
adnan@ubuntu:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_awn-manager.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

---

### Post by moonbeam on 2008-05-02
It is necessary to run awn (the actual dock) at least once before awn-manager (the configuration util).

avant-window-navigator 

Once you've run it at least once then

awn-manager

Should work fine.  This is slated to be fixed in a future revision.

---

### Post by Joeb454 on 2008-05-02
moonbeam is correct :)

I had this issue the first time I installed AWN. Start the dock (you can close it straight away) Then start the Manager :)

---

