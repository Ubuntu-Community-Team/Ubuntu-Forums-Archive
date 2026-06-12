---
title: "[SOLVED] Root to install"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by getitright on 2008-10-07
When attempting to manually install updates to an application I get the message:

"You must be root to install updates."

Is this normal? And can it be bypassed?

---

### Post by NeoTaoistTechnoPagan on 2008-10-07
That's inherent to any Linux distro, you need to be the root user to perform system-wide tasks. 

The simple way around this is to use the "sudo" command (super-user-do)

I would assume that you were trying to use ```
apt-get upgrade foo
```

try it with ```
sudo apt-get upgrade foo
```

it will ask for a password, just enter the pass for your user

---

### Post by Perfect Storm on 2008-10-07
You don't tell how and with what.

If it via commandline you have to use **sudo**

eg;
```
sudo apt-get update
```

---

### Post by NeoTaoistTechnoPagan on 2008-10-07
> **Artificial Intelligence said:**
> You don't tell how and with what.



He did say 'manually install update' - so that would mean CLI.

---

### Post by Dacker on 2008-10-07
yes, sudo will meet your needs because of its availability to access temporarily as a root account and after that will ask for the passwd of your account so this password will be on for 15 minute...
the best place to know more is 
```
man sudo
```

---

### Post by Perfect Storm on 2008-10-07
> **NeoTaoistTechnoPagan said:**
> He did say 'manually install update' - so that would mean CLI.

No he said "manually install updates to **an application**", which can be many things.

---

