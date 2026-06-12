---
title: "permanently change priority of process"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2012-12-13
gmusicbrowser seems to skip or stop playing for a moment when i do somethings
i changed the priority to see if it made a difference and it appears it did but i don't know how to make it permanent
```
sudo renice -n  -13 2888
```
only way i can think of would be to do this from a script that runs as root
```
renice -n  -13 $(pgrep -f /usr/bin/gmusicbrowser)
```

---

### Post by Cheesemill on 2012-12-13
You could edit the /usr/share/applications/gmusicbrowser.desktop file and change the Exec line to something like:
```
Exec=nice -n -13 gmusicbrowser
```This will launch the application with default nice value incremented by -13.

---

### Post by Cheesemill on 2012-12-13
OK, scratch that idea. It still needs to be run as root to have any effect.

I'll keep thinking :)

---

### Post by Cheesemill on 2012-12-13
It's a bit of an ugly hack but you could always run the command you gave in your first post from roots crontab every minute or so.

I'm sure the must be a better way, I'll get back to you if I can figure out what it is.

---

### Post by pqwoerituytrueiwoq on 2012-12-13
This would be nicer i think, i was hoping for a config file for settings default priorities for processes
```
chad@Quantal-Desktop:~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
#display-setup-script=
greeter-setup-script=sh -c "/usr/local/bin/greeter-setup-script &"
session-setup-script=sh -c "/usr/local/bin/session-setup-script &"
session-cleanup-script=/usr/local/bin/session-cleanup-script
chad@Quantal-Desktop:~$ sudo nano /usr/local/bin/session-setup-script
[sudo] password for chad: 
chad@Quantal-Desktop:~$ cat /usr/local/bin/session-setup-script | tail -5
while [ -z "$pid" ];do
    pid=$(pgrep -f /usr/bin/gmusicbrowser)
    sleep 3
done
renice -n -13 $pid

```

---

