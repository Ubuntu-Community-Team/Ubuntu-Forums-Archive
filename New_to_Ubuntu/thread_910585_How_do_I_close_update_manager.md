---
title: "How do I close update manager?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by tallpaul66 on 2008-09-04
I am trying to install Limewire. I downloaded the packet installer but when I run it I get an error message that says "Only one software management tool is allowed to run at one time.Please close the other application e.g. 'Update Manager', 'aptitude', or 'Synaptic' first." Is there a function like XP has where I can see what processes are running and stop something like Update Manager?

---

### Post by rampageoberon on 2008-09-04
```
ps -a
``` or ```
ps aux
``` or ```
gnome-system-monitor
``` will show you all the processes running on your computer.

You can find the process from there. Best to check any "synaptic package manager" and "update manager" windows are closed.

---

### Post by Jack M. on 2008-09-04
Yes, you can go to System > Administration > System Monitor for something similar to the Windows Task Manager. If the message still appears after you've shut down all the processes and/or restarted, though, there might be a bigger problem here. Check back if that's the case!

EDIT: The above works as well, and is most likely better if you need to more comprehensively manage the running processes.

---

### Post by tallpaul66 on 2008-09-04
Thanks for the replies. I went into the system monitor and the only thing I could find that looked okay was update notifier. I killed that but the installer still did not work. I don't know enough about the other stuff in there to try anything else.

---

### Post by tallpaul66 on 2008-09-04
I just tried running the frostwire installer and got the same message. I can't find any of the three programs that the error message suggested in the System Monitor. Does anyone have any other suggestions?

---

### Post by Jack M. on 2008-09-04
If you've tried restarting, then the problem probably lies with the 'administration lock' that prevents two package managers (Update Manager, Synaptic, etc.) from being open at the same time. I don't know too much about this particular aspect of the system, but someone here may. Sorry that I couldn't be more of a help.

---

### Post by tallpaul66 on 2008-09-04
PROBLEM SOLVED!!!  When all else fails read the instructions. The Frostwire people recommended installing JRE. It took me a few tries to get that right but once I did Frostwire installed in about 10 seconds. I appreciate the help that I got here.

---

### Post by Cheesehead on 2008-09-04
Glad you figured it out.
-----------Ignore all below-----------

In System Manager, look for any of the following:
Synaptic
Add/Remove
Update Manager
aptitude
apt-get (any Apt, really)
dpkg
If you find one, terminate it...politely, if possible.
(Update-Notifier is safe; it has nothing to do with the lock)

If you shut down your system for the night, then try tomorrow after a restart. It's shocking how often a good night's rest helps everyone involved.

If it doesn't work tomorrow, then what are your startup apps?
(you might be starting a package manager without knowing it. Good thing to stop doing)

If you still can't do it, then we'll release the lock manually.

---

