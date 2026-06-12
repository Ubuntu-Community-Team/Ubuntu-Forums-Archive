---
title: "update error message"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Wildwest on 2008-07-01
Had a power outage during an update to hardy herron, now error message
says to run dpkg --configure -a to correct the problem. It doesn't. I can no longer update.

---

### Post by sayakb on 2008-07-01
At a terminal:
```
sudo dpkg --configure -a
```

---

### Post by Wildwest on 2008-07-01
I did use the sudo command, to no avail

---

### Post by Wildwest on 2008-07-01
> **LinuxIsInnovation said:**
> At a terminal:
```
sudo dpkg --configure -a
```

I tried the command and it said I had to be a superuser

---

### Post by sayakb on 2008-07-01
Using sudo means you are a superuser (**sudo = **superuser do)
Try:
```
sudo bash
```And then enter your password and you'll see the # prompt. Now do:
```
dpkg --configure -a
```

---

### Post by Wildwest on 2008-07-01
Tried it and no success.

---

### Post by Wildwest on 2008-07-01
A new message says I have to reinstall the package because it was in bad shape.
 How can I go about this?

---

### Post by Wildwest on 2008-07-02
Belated thanks. Computer froze up and I ran out of time. When all else fails follow directions. Your direction to repair this were correct

---

