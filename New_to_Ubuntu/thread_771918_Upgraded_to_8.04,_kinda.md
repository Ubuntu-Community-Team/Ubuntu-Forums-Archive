---
title: "Upgraded to 8.04, kinda"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Turboflame on 2008-04-28
Hardy seems to be working alright right now but I had some trouble during the installation (from online).

Apparently something related to gnome failed to install, I was given the message to go to the synaptic package manager and check the "broken" tab and install it from there. I was also given the message that install was aborting. 

I installed the missing package but I don't know if hardy had finished installing or not. Is there any way to resume a botched install? or to see if the install is complete?

EDIT: This was the file that was broken (from synaptic package manager history)

Upgraded the following packages:
gnome-applets-data (2.20.0-0ubuntu1) to 2.22.1-0ubuntu2

Reinstalled the following packages:
gnome-applets (2.22.1-0ubuntu2)

---

### Post by Turboflame on 2008-04-28
shameless bump

---

### Post by Michael.Godawski on 2008-04-28
Try to check with this command if there are any broken or half-installed packages.

```
sudo dpkg --configure -a
```

---

### Post by Turboflame on 2008-04-28
Well that command didn't seem to display anything so I guess not

---

### Post by Michael.Godawski on 2008-04-28
then you should be fine. :)

---

### Post by Turboflame on 2008-04-28
Ok, thanks :)

---

