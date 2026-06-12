---
title: "windows task scheduler v cron"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by bilboubu on 2012-11-24
On windows I could initiate a task ie a script on idle which would run and stop running if the machine stopped being idle.

Is this possible in linux? At the moment I am running the job every 15 minutes but if I could do it on idle that would be nice.

Would it then be possible to reset the idle timer after it had run?

---

### Post by Lars Noodén on 2012-11-24
You could launch the script or program using [nice](http://manpages.ubuntu.com/manpages/precise/en/man1/nice.1posix.html) with a high number.  That would give the process such a low priority that it would only run when little else is happening.  The higher the number, the lower the priority.

---

### Post by bilboubu on 2012-11-24
Cool, so the script would run when not alot else was occuring, I would have ther script looping , would it then stop the script when the machine became active again, ie user input.

It is more no user input I was looking to link into, I just  read it may be possible in conjuntion with a screen saver?

---

### Post by Lars Noodén on 2012-11-24
The system would automatically control the script's activity with 'nice'.  I'm not sure how the screen savers are set up but they should be niced, too.  Otherwise, they will take priority over your script.  Some screen savers are real CPU hogs.

---

