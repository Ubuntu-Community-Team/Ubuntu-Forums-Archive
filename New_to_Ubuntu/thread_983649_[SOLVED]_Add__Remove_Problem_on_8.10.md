---
title: "[SOLVED] Add / Remove Problem on 8.10"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by H3retic on 2008-11-15
Thanks to this, I'm debating whether to go back to 8.04.  Has this issue been resolved already?

---

### Post by taurus on 2008-11-15
Do you have synaptic or adept running in the background?  This has nothing to do with whether you are running Intrepid or Hardy.

---

### Post by bumanie on 2008-11-15
Suspect you have synaptic open at the same time as trying to run add/remove. Only one package manager can operate at the one time.

---

### Post by H3retic on 2008-11-15
> **bumanie said:**
> Suspect you have synaptic open at the same time as trying to run add/remove. Only one package manager can operate at the one time.

How can you tell which are open at the same time?

---

### Post by taurus on 2008-11-15
Applications -> Accessories -> Terminal
```
ps -A
```
Look at the output from the command above and see if you see any synaptic, apt-get, apt, or adept.

---

### Post by H3retic on 2008-11-15
I did a reboot, and it fixed the issue.  Now, in the output there is only -synaptic.

Looks like I posted too early ;)

Thanks for the help.

---

