---
title: "how to use hddtemp????????"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by coolman121$ on 2008-07-16
im am still unaware of how to use hddtemp i need this answer

---

### Post by Morpheun on 2008-07-16
> **coolman121$ said:**
> im am still unaware of how to use hddtemp i need this answer

```
 sudo hddtemp /dev/sd*
```

Usually sda, although obviously if you want to see the info for a different hdd adapt accordingly

---

### Post by Morpheun on 2008-07-16
actually "sd*" would be a viable command come to think of it, it would just list information for all your hard drives

---

### Post by coolman121$ on 2008-07-16
thanks but is there any graphical way to find it normally changing

---

### Post by Morpheun on 2008-07-16
There is no default GUI for hddtemp

```
watch -n5 sudo hddtemp /dev/sd*
```

That will run it every 5 seconds and display the output constantly in a terminal session. I'm sure there are flashier options but none more reliable.

---

### Post by m_duck on 2008-07-16
You could probably install the system monitor "conky" to show the temps on ur desktop. I'm not sure if hddtemp is built in or not but I would imagine you could use the "execi" function in conky. A good thread with loads of info is [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by ebe326 on 2008-07-16
I use sensors-applet. It's in the repository. Install it then right click on the panel you want it on and add it. It shows up in the applet box as Hardware Sensors Monitor.

david

---

### Post by kansasnoob on 2008-07-16
I've had excellent luck installing 
> computertemp
from Synaptic.

You can then right click on an open space in either panel, select "Add to Panel" and see this:

[ATTACH]77988[/ATTACH]

Add the Comp. Temp. Monitor then you'll see it in whatever panel you added it to, and if you right click it and click on preferences you can change things:

[ATTACH]77985[/ATTACH]
[ATTACH]77986[/ATTACH]
[ATTACH]77987[/ATTACH]

---

