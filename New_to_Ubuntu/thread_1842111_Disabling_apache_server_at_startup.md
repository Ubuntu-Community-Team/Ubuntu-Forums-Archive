---
title: "Disabling apache server at startup"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by aura7 on 2011-09-10
Can anyone suggest an easy way to disable apache server from running at startup in ubuntu.

Or not just apache any service from running at startup in ubuntu.

---

### Post by _d_ on 2011-09-10
You can try boot-up manager:

```
sudo apt-get install bum
```

Or search for bum via Synaptic.

---

### Post by rolandrock on 2011-09-10
Some services are started from System/Preferences/StartupApplications, some are controlled from more esoteric rc scripts or init.d (explore under /etc tree).

Also, see:

```
man service
man apache2ctl
```

If these hints aren't adequate, please reply with your Ubuntu version, apache version and hope that some kindly Wizard sees your post.

Good luck.

---

### Post by aura7 on 2011-09-11
Thanks _d_  I was actually looking for something like this as I manually edit from a GUI.

I consider this thread solved

---

### Post by papibe on 2011-09-11
First stop the service:
```
$ sudo service apache2 stop
```
or this:
```
$ sudo /etc/init.d/apache2 stop
```
Then remove it from the services list:
```
$ sudo update-rc.d -f apache2 remove
```
That is it.
In case you change your mind sometime, you can add it again like this:
```
$ sudo update-rc.d apache2 defaults
```
Hope it helps,
Regards.

---

