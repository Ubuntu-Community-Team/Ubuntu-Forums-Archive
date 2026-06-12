---
title: "[SOLVED] Infinite loop in Bash - How to?"
date: 2007-10-03
forum: Programming Talk
---

### Post by dwhitney67 on 2007-10-03
Normally one would frown upon intentionally programming an infinite loop, but that is exactly what I need to prevent a shell script from exiting when it has "concluded" its task.

So my question is, how do I code an infinite loop in Bash script?

Note:
I have been working on the joyful task of producing a bootable CD-R that can either install a customized Linux distro onto the HDD or merely provide the operator with access to a Busybox shell.  In either case, when the task is complete, I receive a "Kernel panic - not syncing: Attempted to kill init".  I have spent countless days troubleshooting this damn little error that I've concluded that perhaps it would be easier to simply put a "band-aid" over it so that it never occurs.

---

### Post by slavik on 2007-10-03
while true; do
#code
done

edit: fixed the code :)

---

### Post by dwhitney67 on 2007-10-03
Thanks, that'll work just fine!  I'll slap a 'sleep 60' in there for the code-section.

---

