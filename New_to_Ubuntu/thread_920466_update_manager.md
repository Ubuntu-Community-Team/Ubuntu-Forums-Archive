---
title: "update manager"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by cross1010 on 2008-09-15
hi there .I'm very new to ubuntu. when i open my update manager and check for new updates . it does not  respond properly . it says dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem . what must i do . and where do i have to run that command .

---

### Post by kpkeerthi on 2008-09-15
Open a terminal (Applications -> Accessories -> Terminal) and enter this command:
```
sudo dpkg --configure -a
```

This should sort things out.

---

### Post by Sycron on 2008-09-15
Go to Appliations-->Accesories-->Terminal and type ```
sudo dpkg --configure -a
```

---

### Post by cross1010 on 2008-09-15
thank you sir .

---

### Post by cross1010 on 2008-09-15
thank you for your help

---

