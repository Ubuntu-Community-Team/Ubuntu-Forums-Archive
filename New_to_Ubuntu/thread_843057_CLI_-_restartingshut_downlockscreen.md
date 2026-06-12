---
title: "CLI - restarting/shut down/lockscreen"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-27
how does one restart/shutdown/and lockscreen respectively, from the terminal?

---

### Post by luisito on 2008-06-27
Try all the scripts in /etc/acpi/

---

### Post by ChompTheMan on 2008-06-27
To shutdown in the CLI just type *shutdown*.  If you want to reboot, then *shutdown -r*.  Not sure about lockscreen.

---

### Post by luisito on 2008-06-27
Actually to reboot is
reboot

to shutdown
shutdown now

to turn off screen
/etc/acpi/screenblank.sh

---

### Post by webofunni on 2008-06-27
In Ubuntu Hardy Following will lock screen : 

```
gnome-screensaver-command  --lock
```

---

### Post by sam_delta on 2008-06-27
the following will also work

to shut down
```
sudo init 0
``` 

to restart
```
sudo init 6
```

sam

---

### Post by dwhitney67 on 2008-06-27
[post deleted].

---

