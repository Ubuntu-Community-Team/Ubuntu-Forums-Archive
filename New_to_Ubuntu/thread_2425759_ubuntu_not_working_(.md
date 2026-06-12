---
title: "ubuntu not working :("
date: 2019-08-29
forum: New to Ubuntu
---

### Post by nidhal123 on 2019-08-29
[ATTACH=CONFIG]283895[/ATTACH][ATTACH=CONFIG]283896[/ATTACH][ATTACH=CONFIG]283897[/ATTACH]
i just installed python , katoolin and (s)aint , restarted the machine and i got this
any idea on how to fix this ?

---

### Post by cruzer001 on 2019-08-29
Cups is the printer service and NetworkManager is of course network control.  Your machine should still boot with these fails.  Does it?

Katoolin and (s)aint is cybersecurity, something I do not run.  Did you research this before installing?  Whats python got to do with any of this?  Its better to install such packages one at a time, then if trouble appears you know what package did it.

And its always a nice touch to post what your running and the version.

Sorry, but I do not have a magic answer for you.  Maybe someone else will.

---

### Post by TheFu on 2019-08-29
Use a different tty and login. Then you can check the log files for the issues.

Change ttys by using <alt><cntl>-F1, F2, F3, ... 
May need to hit <enter> to get a login prompt.

---

