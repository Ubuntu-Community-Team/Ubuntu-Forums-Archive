---
title: "Uninstall Terminal Code"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-08-20
Is there a terminal code to uninstall a program. Thanks.

---

### Post by kirsis on 2008-08-20
sudo aptitude remove <package-name>

---

### Post by kamitsukai on 2008-08-20
```
sudo apt-get remove *program name here*
```

---

### Post by redfox1160 on 2008-08-20
thanks

---

### Post by kiridude on 2009-03-26
As kirsis said, sudo aptitude remove <name> is the way to go.

---

### Post by maxwelldeaton on 2011-10-11
The sudo aptitude didn't work for me but the apt-get did. Is there a reason for that?

---

### Post by ubudog on 2011-10-11
> **maxwelldeaton said:**
> The sudo aptitude didn't work for me but the apt-get did. Is there a reason for that?

This thread is old.  The syntax for aptitude would be:
```

sudo aptitude remove packagename

```

If you have more questions, please start a new thread.  Thanks!

Thread closed.

---

