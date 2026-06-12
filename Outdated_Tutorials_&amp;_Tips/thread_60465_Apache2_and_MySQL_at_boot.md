---
title: "Apache2 and MySQL at boot"
date: 2005-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by dbeckham32 on 2005-08-27
Can anyone please tell me how to disable Apache2 from starting up automatically when I reboot? I'd prefer to manually start it when needed.

Have not yet been able to find newbie-centric instructions on how to to this.

Thanks in advance!

---

### Post by dbeckham32 on 2005-08-27
And sorry in advance for asking a question in this forum. Just spotted the sticky above. Crap.

---

### Post by munitras on 2005-08-28
hey.

i'm no expert, but try

```
sudo vi /etc/default/apache2
``` 

change 

```
NO_START=0
``` 

to 

```
NO_START=1
```

---

### Post by Spudgun on 2005-08-28
Try this:

```
sudo update-rc.d -f apache2 remove
```
```
sudo update-rc.d -f mysql remove
```

Hope it works!!

---

