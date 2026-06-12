---
title: "[SOLVED] why dont i see a quit button?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by brandon333 on 2008-08-28
i see switch user, log out, suspend, hibernate, how do i turn ubuntu, my computer off..

oddest thing ever


i mean do i have to log out to main screen and then power down? I sware last time i had ubuntu there was a quit button

---

### Post by iaculallad on 2008-08-28
> **brandon333 said:**
> i see switch user, log out, suspend, hibernate, how do i turn ubuntu, my computer off..

oddest thing ever

System->Administration, "Local" tab, check "Show Menu Action Bar" in Menu Bar. Click on Close.

---

### Post by jamesrl on 2008-08-28
Is this your own computer, and are you system admin?  Frequently, machines that aren't supposed to be shutoff/rebooted by average users have those functions disabled.  You can go to the command prompt and type

```
sudo shutdown now

```
or 
```
sudo reboot

```
if you need to shutdown or reboot.

---

### Post by Ryadt on 2008-08-28
Under the 'Local' tab in 'Login window' ( System > Administration > Login window), make sure both options in 'Menu Bar' is checked.

---

### Post by brandon333 on 2008-08-28
ha..I knew it was there...thanks for the fast responses..

---

