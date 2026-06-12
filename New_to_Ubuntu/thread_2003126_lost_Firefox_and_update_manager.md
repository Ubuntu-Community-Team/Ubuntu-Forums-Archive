---
title: "lost Firefox and update manager"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by hodgesse on 2012-06-13
Hi!

I have Ubuntu 12.04 and it locked up during an update.  I restarted the system and now the Firefox and Update Manager icons have disappeared.

How do I get them back, please?

Thanks,
Erin

---

### Post by wilee-nilee on 2012-06-13
> **hodgesse said:**
> Hi!

I have Ubuntu 12.04 and it locked up during an update.  I restarted the system and now the Firefox and Update Manager icons have disappeared.

How do I get them back, please?

Thanks,
Erin
Try hitting the alt-f2 keys then type in unity --reset

Or run the reset in a terminal.

You may need to restart the update here are two commands to use.
```
sudo dpkg --configure -a
```                      
 ```
sudo apt-get -f install 
```

---

### Post by daslinkard on 2012-06-14
I've had similar issues with 12.04 locking up.  I kept it on my system for about 4 days then decided to go back to 11.10 and for the past 3 weeks....knock on some wood....no issues running 11.10!!!!

---

