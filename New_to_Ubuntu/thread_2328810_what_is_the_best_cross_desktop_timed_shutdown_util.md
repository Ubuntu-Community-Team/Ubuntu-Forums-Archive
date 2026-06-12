---
title: "what is the best cross desktop timed shutdown utility?"
date: 2016-06-24
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-06-24
i run various ubuntu destops(lubuntu xubuntu etc) and would like to find a timed shutdown utility that will work best on all of them?

ive looked at qshutdown and gshutdown... so far any others?

( i know this will be personal preference...but im looking for opinions.)

---

### Post by QDR06VV9 on 2016-06-24
What I use is not a utility but just a basic terminal command:
```
sudo shutdown -h 120
```
Where the number 120 is equal to minutes.
Just my 2 cents worth.

---

### Post by Frogs Hair on 2016-06-24
Commands and scripts are a possibility in place of an application .

[http://unix.stackexchange.com/questions/120506/how-to-shutdown-linux-at-a-specific-datetime-from-terminal/120509](http://unix.stackexchange.com/questions/120506/how-to-shutdown-linux-at-a-specific-datetime-from-terminal/120509)

---

### Post by ajgreeny on 2016-06-24
> **runrickus said:**
> What I use is not a utility but just a basic terminal command:
```
sudo shutdown -h 120
```
Where the number 120 is equal to minutes.
Just my 2 cents worth.
My choice as well when I need to do this.  You can even use it in a script and double click on it or make a desktop link/launcher to it if you wish.

You might also like to look at the following commands which do not require a password; I've not looked at them for a long time but they did work in the past.  
```
To suspend
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
To shutdown
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
To hibernate
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate
```

The loss of hal in the system in more recent versions may stop these from working, but if they do still work you could use them with the sleep option eg ```
sleep 120m;dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

EDIT:
Just tried this on my 14.04 where it does still work though bear in mind that I do have hal installed from the ppa at [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu)

---

