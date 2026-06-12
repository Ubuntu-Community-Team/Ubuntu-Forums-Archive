---
title: "Stop password prompt when using update manager etc...?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by willemmerson on 2008-11-19
Is it possible to stop ubuntu prompting for password when using update manager, etc? I don' mind being prompted once when I first turn the computer on but it gets annoying being asked every time I use sudo.
I'm using 8.04.

---

### Post by rampageoberon on 2008-11-19
you can modify the /etc/sudoers file to match the command you don't want to be asked for a password.

Its not recommended unless you know what you are doing. Allowing everything can compromise your system

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

Edit: Alternatively you could add the following job to crontab and set to run as root (run it periodically how you feel). You won't need the graphical update manager then.

```
aptitude update && aptitude upgrade && aptitude full-upgrade && aptitude clean
```

---

