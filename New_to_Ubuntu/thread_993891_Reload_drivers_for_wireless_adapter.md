---
title: "Reload drivers for wireless adapter??"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by agwblack on 2008-11-26
Hi all. Very new here. Recently installed Ubuntu 8.10 (my first go at Linux after I gave up on Vista), and most stuff worked quite well. That which didn't work straight away I have been gradually ironing out (with much help). 

One problem (which has been discussed elsewhere by others) is the tendancy for my connection to my wireless network to die, after anything between 5mins and 90mins. This is fixed if I reboot my computer. My question is: Is there a way to re-enable my wireless adapter without having to shutdown and restart the whole system?

Thanks in advance

---

### Post by TFX360 on 2008-11-26
There is.

In a Terminal do:

```
/etc/init.d/networking restart
```

This should bring you back to the start-up equivalent.

---

### Post by agwblack on 2008-11-26
Beautiful, thank you :)

---

### Post by TFX360 on 2008-11-26
You're welcome! Maybe in the future you can help someone else with this. Most services can be restarted/stopped/started via /etc/init.d/"servicename" restart/stop/start.

---

