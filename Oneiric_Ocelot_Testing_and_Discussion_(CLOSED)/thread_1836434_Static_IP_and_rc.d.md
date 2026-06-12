---
title: "Static IP and rc.d"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Beeblebrx on 2011-08-31
Two strange problems:
1. I would like to prevent certain services from starting up.  I have gone through all of the rc's (rc.0 -> rc.S), but the services I am looking to prevent from starting up are not listed there (like avahi & modem manager).  This also fails:
> sudo update-rc.d avahi-daemon disable
update-rc.d: warning: /etc/init.d/avahi-daemon missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
System start/stop links for /etc/init.d/avahi-daemon do not exist.
2. Trying to set static IP through [COLOR=DarkGreen]/etc/network/interfaces [/COLOR]fails miserably with some message like eth0 - unknown interface when I run [COLOR=DarkGreen]# ifconfig eth0 up[/COLOR].

---

### Post by cariboo on 2011-08-31
What you are trying to do hasn't worked for several releases, if you want to stop the modem manager and the avahi-deamon, just remove the executable bit from /etc/init.d/modemmanager and /etc/init.d/avahi-daemon. Ubuntu has used [upstart]("http://upstart.ubuntu.com/") for quite a while to start services.

To set a static ip address, use Network-Manager, instead of /etc/network/interfaces.

---

### Post by sisco311 on 2011-08-31
You can use an .override file to disable an upstart job: [http://upstart.ubuntu.com/cookbook/#override-files](http://upstart.ubuntu.com/cookbook/#override-files)

```
echo 'manual' | sudo tee /etc/init/**job-name**.override
```

---

### Post by Beeblebrx on 2011-08-31
Thanks both of you for the input - solved.

---

