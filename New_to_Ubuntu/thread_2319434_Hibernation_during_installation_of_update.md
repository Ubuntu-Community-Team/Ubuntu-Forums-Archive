---
title: "Hibernation during installation of update"
date: 2016-04-04
forum: New to Ubuntu
---

### Post by Maria_Jensen on 2016-04-04
This morning I attempted to update to version 15.10. However during the process the computer went into the power saving hibernation mode. Everything froze, so I had to restart it. 

When it happened the downloading part was done and it was about 2/3 into installing. It seems to be working fine after restarting. The log in screen says version 15.10. 

But is there any command I can use to make sure that the rest of the installation process takes place? Or possibly start the update over, this time with hibernation disabled?

---

### Post by grahammechanical on 2016-04-04
I am glad that the OS is loading to a working desktop. It makes things easier. Open the terminal & run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If you see messages about broken packages then run this

```
sudo apt-get install -f
```

You most likely will see a message about packages that are no longer required. This is the command to remove them

```
sudo apt autoremove
```

Regards

---

### Post by Maria_Jensen on 2016-04-04
Thank you so much.

---

