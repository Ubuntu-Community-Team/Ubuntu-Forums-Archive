---
title: "log file viewer window is blank"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by boregard on 2011-10-17
ok, when i enter ```
 gksudo gnome-system-log & 
``` the log file viewer window opens but it is blank. anyone know how i can fix this problem?

---

### Post by Derek Karpinski on 2011-10-20
blank here too.:(

---

### Post by boregard on 2011-10-21
> **Derek Karpinski said:**
> blank here too.:( is your startup applications window blank also?

---

### Post by howefield on 2011-10-21
Bug report here for the blank log file viewer..

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/841085](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/841085)

but if you want to populate your startup applications, run the following two terminal commands..

```
cd /etc/xdg/autostart/
```
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

### Post by boregard on 2011-10-21
> **howefield said:**
> Bug report here for the blank log file viewer..

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/841085](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/841085)

but if you want to populate your startup applications, run the following two terminal commands..

```
cd /etc/xdg/autostart/
``````
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
``` thanks,i've already ran those two cmds. startup apps. is working fine now.

---

