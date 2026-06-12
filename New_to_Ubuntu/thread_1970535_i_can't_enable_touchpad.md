---
title: "i can't enable touchpad"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by suarez on 2012-05-01
[CENTER]my touchpad is disabled and i can't enable it
Problem is that it works well at the start (Before entering the password)
 But after going to the desktop does not work

**Touchpad stops working immediately after login**
Any help please

[/CENTER]

---

### Post by cortman on 2012-05-01
Have you tried enabling it from system settings?
What happens if you run

```
synclient TouchpadOff=0
```

in a terminal?

---

### Post by suarez on 2012-05-01
[CENTER]I am using touchpad-indicator and if enabled it nothing happens
[/CENTER]

---

### Post by suarez on 2012-05-01
[CENTER]synclient TouchpadOff=0

:( nothing
[/CENTER]

---

### Post by suarez on 2012-05-01
[CENTER]for the touchpad has a simple solution, you will open the terminal (ctrl+alt+T), type sudo gedit /etc/rc.local 
and edit the file wich opened. Before the line exit 0 you will add the following lines: 
 sudo modprobe -r psmouse
 sudo modprobe psmouse proto=imps
 Save the file and reboot the computer[/CENTER]

---

### Post by cortman on 2012-05-01
What version of Ubuntu are you using?
Do you get an error message from the synclient command, or does it execute ok and not affect anything?

---

### Post by cariboo on 2012-05-01
Merged two threads on the same subject.

---

