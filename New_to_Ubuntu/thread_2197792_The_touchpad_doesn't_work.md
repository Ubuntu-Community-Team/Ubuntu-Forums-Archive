---
title: "The touchpad doesn't work"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2014-01-05
I have tried to actualized my netbook with OS 12.4 and it has experienced a problem: It says to me about the problem: Executablepath /usr/bin/aptd/  Now the touchpad doesn't work. Fortunately I can use an external mouse. Can anyone help me solve it
Thanks

---

### Post by varunendra on 2014-01-05
It may help if you show us the following outputs from a terminal (Ctrl-Alt-T) -
```
xinput
synclient
cat /proc/bus/input/devices
grep -i touchpad /var/log/Xorg.0.log
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

