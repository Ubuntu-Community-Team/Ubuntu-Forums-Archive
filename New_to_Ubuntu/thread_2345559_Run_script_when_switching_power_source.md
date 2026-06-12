---
title: "Run script when switching power source"
date: 2016-12-05
forum: New to Ubuntu
---

### Post by Vidar30 on 2016-12-05
Ubuntu 16.10 

I want to run commands when switching to battery on my laptop. Got a standard script in /etc/pm/power.d which works fine when I in terminal execute pm-powersave true/false. The scripts in /etc/pm/power.d are not executed on switching power source. Right now I need to execute them manually. I thought these scripts were sent a true/false depending on power modus, but not so?

---

### Post by kevdog on 2016-12-06
I'd take a look at this posting to get you started: [http://askubuntu.com/questions/609695/does-systemd-read-etc-pm](http://askubuntu.com/questions/609695/does-systemd-read-etc-pm).  It's not exactly what you want, however since Ubuntu uses systemd now rather than systemV, your going to have to a write a systemd unit service file.  An example is in the post I linked.  Another example of the systemd unit file I wrote, emails and texts me every time the OS is either booted or shutdown -- I did this to know if the server shutdown unexpectedly because of a power loss. An example of this script is found here --   [https://ubuntuforums.org/showthread.php?t=2339386](https://ubuntuforums.org/showthread.php?t=2339386).  You will either have to google, look around, or modify a script to get exactly what you want.

---

