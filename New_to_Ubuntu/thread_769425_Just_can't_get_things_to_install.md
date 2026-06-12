---
title: "Just can't get things to install"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-26
Hey
I just can not get things to install...

There is always a message that other installations are running and that there is some Java script missing.

I have tried the following but with no luck.

 Re: installing plugins
After running
Code:

sudo dpkg --configure -a

make sure you update everything, run
Code:

sudo aptitude update

and
Code:

sudo aptitude dist-upgrade

__________________

---

### Post by Joeb454 on 2008-04-26
If other upgrade managers are running, you could try rebooting, then try installing again and see what happens :)

---

### Post by SunnyRabbiera on 2008-04-26
odd, did you try to re install java?
you may see some issues in the next few days thanks to the current server overload

---

### Post by Michael.Godawski on 2008-04-26
Can you please post the exact error message?

---

### Post by saskatchewan on 2008-04-26
I have tried rebooting several times
I hope that I do not have to reinstall the OS just so that I can install updates.

---

### Post by saskatchewan on 2008-04-26
When I go to the add/remove list/function it won't let me install or uninstall anything.

---

### Post by saskatchewan on 2008-04-26
Here is the exact error message when I try going through add/remove.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by joshsmith on 2008-04-26
run sudo dpkg --configure -a
in a terminal window, and post the output

---

### Post by saskatchewan on 2008-04-26
I think that the problem is limewire and I am reinstalling the OS to cure it.

---

