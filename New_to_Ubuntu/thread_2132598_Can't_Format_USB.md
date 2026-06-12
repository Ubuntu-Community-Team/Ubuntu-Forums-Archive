---
title: "Can't Format USB"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by ctbuzzy on 2013-04-05
I'm running Ubuntu 12.04. I'm trying to format a USB drive but it won't let me. I know this question has been asked repeatedly & answered, but none of the solutions comes close to working for me.  The USB mounts just fine, & I can access its current contents (it was formatted in Win7). But when I try to format it using Disk Utility, it gives me an error message telling me "the device is busy."  I've followed suggestions to dismount the drive by ejecting it. This just creates a new error: "The operation failed." I've follwed suggestions to dismount it by safely removing it. This makes it disappear so it's inaccesible to Disk Utility. Remounting it does nothing. I've attempted suggested command line approaches - no dice. And reboots do nothing.  What am I missing? Can anyone help? This is rather important. Thanks!

---

### Post by carl4926 on 2013-04-05
Install gparted
Unmount it from gparted
then format and apply

---

### Post by ctbuzzy on 2013-04-05
Worked like a charm! You're a lifesaver. Thanks!

---

### Post by carl4926 on 2013-04-05
> **ctbuzzy said:**
> Worked like a charm! You're a lifesaver. Thanks!No worries

---

