---
title: "Password Problem"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by nirakarsethy on 2008-04-25
Whenever I want to go to the SU mode it asks for a password. But the Problem is it doesn't take my given password. While installation Ubuntu asked once for the password. I'm giving the same but its not accepting ?

---

### Post by amingv on 2008-04-25
If you're typing
```
su
```

try
```
sudo su
```

---

### Post by Monicker on 2008-04-25
Are you trying to SU or SUDO?  There is a big difference.  Su means that you have to enter the root password, which in Ubuntu does not really exist.  You need to use sudo.

---

### Post by Dr Small on 2008-04-25
Try:
```
sudo su
```

---

### Post by Gazneth on 2008-04-25
Or try ```
sudo -i
``` that gives you a root prompt, using your normal administrative password. To open a root nautilus session, which can be handy at times type ```
gksudo nautilus
```. A root nautilus session will allow access to files with root permissions using the GUI. Use these amazing powers carefully.

---

### Post by Joeb454 on 2008-04-25
If want to become root for something, I always use ```
sudo -i
``` Though just be careful what you do as root :)

Hope this helps

---

### Post by nirakarsethy on 2008-04-26
Thanks

---

