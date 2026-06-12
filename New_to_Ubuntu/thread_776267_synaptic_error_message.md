---
title: "synaptic error message"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by DarinB on 2008-04-30
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by bluefrog on 2008-04-30
have you done what you were told to do?

open applications/accessories/terminal, write
sudo dpkg --configure -a        and hit enter on your keyboard

---

### Post by DarinB on 2008-04-30
i got this response sorry i didn't understand the instructions what now????

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

---

### Post by DarinB on 2008-04-30
after two crash reports i was able to remove the broken java6 bin package
now it is running and i was able to boot up.
I am not sure what happened
.....i did try to install flash 9 but it would not finish.
maybe the java6 bin package was messed up.
everything seems to work
is my assessment reasonable?

---

### Post by tiggsy on 2008-05-07
i got this after running the instructions on this page: 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
after which i got a licensing screen on the terminal which would not allow me to accept it, and following which i kept getting an error message about something being locked, when there should have been nothing using it.

The license was for java6 so I'm assuming its the same problem.

Would be helpful if someone would give a reply. I have this message about "you have 1 broken package, use broken to find it" which is less than helpful. No idea what i am supposed to do to find it!


**update** For other newbies who get same problem, open Synaptic (in System->Administration) and go to Edit-> Fix broken packages and Apply
this fixes the broken packages message. phew

---

