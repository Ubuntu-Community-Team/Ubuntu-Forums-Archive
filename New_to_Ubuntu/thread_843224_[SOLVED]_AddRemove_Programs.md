---
title: "[SOLVED] Add/Remove Programs"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by lyni on 2008-06-28
I just went into the Add/Remove program and I get this error message -

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what does it mean and where do I manually run it?
any assistance is greatly appreciated because I am still trying to understand ubuntu.

thank you
lyn

---

### Post by lisati on 2008-06-28
This should help:

Open up a terminal (in Ubunutu it's on the System->accessories menu), and enter ```
sudo dpkg --configure -a
```You will be asked for your password, which will be invisible while you type.

EDIT: Thanks, [iaculallad]("http://ubuntuforums.org/member.php?u=520984"), I forgot to say to retry the Add/Remove programs!

---

### Post by iaculallad on 2008-06-28
> **lyni said:**
> I just went into the Add/Remove program and I get this error message -

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what does it mean and where do I manually run it?
any assistance is greatly appreciated because I am still trying to understand ubuntu.

thank you
lyn

Open up your terminal and issue the command below as suggested by the error message:

```
sudo dpkg --configure -a
```

Then try to open your Add/Remove Program.

---

### Post by lyni on 2008-06-28
thank you lisati and iaculallad it worked.
lyni

---

### Post by NovaAesa on 2008-06-28
Please remember to mark your thread as solved. =D

---

