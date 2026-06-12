---
title: "I can't install any software! Pleas help?!"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by User2011 on 2011-09-23
[FONT=Arial Narrow][SIZE=2]Okay, so every software that I try to download on the **Ubuntu Software  Center** is consequently being interrupted by a pop up error window that  says:

***An unhandlable error occured -*** [I]There seems to be a  programming error in aptdaemon, the software that allows you to  install/remove software and to perform other package management related  tasks

[B]Details:
[FONT=Courier New]
[/FONT][/B][/I][FONT=Courier New]Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.



[FONT=Arial Narrow]Can anybody please help me? Thankyou.[/FONT]
[/FONT]
[/SIZE][/FONT]

---

### Post by Antarctica32 on 2011-09-23
IS this a fresh install? if not how long have you been using it? 
Something like this happened to me before. I Installed on a laptop and i couldn't install so I just re installed but that didn't fix it so I wiped the whole drive and then I reinstalled and it worked. if you do decide to reinstall use a different CD or wipe your usb stick and then put ubuntu back on it and then try it. If you need help just ask. I am going on a trip for the weekend though, so i won't be able to reply for a while.

---

### Post by User2011 on 2011-09-23
[SIZE=2]Yes! This is a fresh install. I've just installed Ubuntu 11.04 for the second time today. I had some previous issues this morning in which I wasn't being able to solve, therefore I reinstalled Ubuntu 11.04 and everything is working perfectly fine now, of course, except for this error window which apparently doesn't let me download any software from the *Ubuntu* *Software Center*[/SIZE]...

---

### Post by ajgreeny on 2011-09-23
Can you run ```
sudo apt-get update
``` and then ```
sudo apt-get upgrade
```in terminal and tell us if any errors appear from that.

If that still causes problems run synaptic instead of the software-center and go to **Edit ->Fix broken packages**.  That may solve the problem.

---

### Post by User2011 on 2011-09-23
I opened the terminal and applied the codes and everything worked well. I ended up with an "EULA" page about Ending User License Agreements for Microsoft. However, I tried to download a software on Ubuntu Software Center and the same error window popped up again! More over I tried opening the *Synaptic *as said and another window popped up informing me that I already have a (like apt-get or aptitude) running, but I believe not!

---

### Post by ajgreeny on 2011-09-24
That EULA you see is because the [FONT=Verdana][SIZE=1]ttf-mscorefonts-installer requires it to be agreed.  In the screen that appears press tab until the OK at the bottom shows highlighted then hit Enter.  The ttf package will then be installed.

As for the two applications running, it can be that update-manager has started in the background, or something similar to that.  A reboot will overcome the problem normally, but you may also be able to stop the program, whatever it is in system-monitor.
[/SIZE][/FONT]

---

### Post by Birchle on 2011-09-24
> **User2011 said:**
> I opened the terminal and applied the codes and everything worked well. I ended up with an "EULA" page about Ending User License Agreements for Microsoft. However, I tried to download a software on Ubuntu Software Center and the same error window popped up again! More over I tried opening the *Synaptic *as said and another window popped up informing me that I already have a (like apt-get or aptitude) running, but I believe not!
Close Ubuntu Software Center before trying to open Synaptic.  Both use apt-get in the background, so if either one was open when you tried to open the other, the popup was giving you correct (if unclear to new users) information.

---

