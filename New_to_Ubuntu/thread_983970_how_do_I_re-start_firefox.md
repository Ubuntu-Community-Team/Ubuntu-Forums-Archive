---
title: "how do I re-start firefox?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by baracuda68 on 2008-11-16
Hi.
After a Firefox3 crash, I try to start firefox again, I get "Firefox is already running.Please close Firefox or restart your system" or something similar... But the deal is... I run the "top" command in terminal, and any form of firefox is not running. 
I try "killall firefox", but 'no process killed'.
I try "killall firefox-bin". seems like it kills, but I still get the message above.

Any hints, other than restarting X?
Thanks:confused:

---

### Post by oilchangeguy on 2008-11-16
just reboot the computer

---

### Post by alienexplorers on 2008-11-16
I agree with oilchangeguy a restart will fix your problems.  This seems very common in Firefox.

---

### Post by gettinoriginal on 2008-11-16
you can also go to System > Admin > System Monitor > Processes, and kill it there

---

### Post by Lakeside5 on 2008-11-16
I have the same problem. But it happens so often, aww gee, surely there`s a better way than constantly re-starting? thanks :)

---

### Post by CatKiller on 2008-11-16
Delete the ~/.mozilla/firefox/*profile*.default/lock file.

---

### Post by scorp123 on 2008-11-16
> **oilchangeguy said:**
> just reboot the computer Overkill!! **This is not Windows!**

A Linux system only needs rebooting when and if there is a serious hardware problem (e.g. disks failing, RAM chips getting corrupted, CPU overheating ...) or if you messed with the kernel (e.g. you just installed a new one).

**Anything and everything else can be done _WITHOUT_ rebooting.**

---

### Post by scorp123 on 2008-11-16
> **baracuda68 said:**
>  After a Firefox3 crash, I try to start firefox again, I get "Firefox is already running."  The "top" command only gives you the most active tasks .... not the complete list! It would be better if you checked with e.g. this command:  ```
ps -efH
``` ... This would give you the list of all running programs in a tree-like fashion. Try it out.

If that output looks too complicated for you, you can add a filter via "grep" and thus filter out just the bits you care about, e.g. ```
ps -efH | grep firefox 
``` ... If there is any bit of firefox still running it should show up there, and with the help of the "PID" number (second column on the left) you should be able to kill it if it is hanging.

Other ways to kill stuff:  **pkill**

**pkill** can kill stuff based on a pattern ... e.g. ```
pkill 'firefox*'
``` should instantly kill anything that starts with "firefox", e.g. "firefox", "firefox-bin", "firefox-helper" and whatever their names may be.

You can also completely kill all programs based on user ID's, e.g.
```
pkill -U joeuser
``` ... kills all programs of the "joeuser" account.

It should not be necessary ever to reboot your entire system just because of a hanging web browser ;)

---

### Post by SIGTERMer on 2008-11-16
people, i agree that restarting your pc just because of a proc. gone wild is overkill.
when you try to run a program you just forced to quit, and it complains that you are still running it, that simply means that the main process is still running! just open the gnome-system-manager and find the guilty process (which in your case is firefox) under the processes tab and kill it!

______________
by the way, if you need to restart your system (shutting down all non-essential processes, including x), type 
sudo init 1
when it finish going into that mode, restart everything by typing: sudo init 5. or if that nice blue screen shows up, chose start up normally :)

*edit*
just seen the post before me, nice.. but mine way is more easer for new users (GUI) :)

---

### Post by Wickd on 2008-11-16
I had exactly this problem and found the google toolbar was the little ******* behind it. Any chance that you are running the google bar?

---

### Post by aulio on 2008-11-26
I have this problem even if I quit firefox from the File menu. The processes always remain running and I have to kill them by myself.

Any idea why the *quit* doesn't work?

---

