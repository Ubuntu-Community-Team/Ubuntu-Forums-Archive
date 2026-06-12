---
title: "How to change lubuntu runlevel at Boot"
date: 2021-07-31
forum: New to Ubuntu
---

### Post by fausto99 on 2021-07-31
I'm running a local apache server on a puny old laptop which has a lubuntu OS.
I don't need a GUI. Can I get the laptop to boot up in runlevel 3 (but still starting up apache)?

Google searches and YT keep mentioning a file called inittab but lubuntu doesn't seem to have one

p.s. I'm new to Linux but was a reluctant sys admin for a couple of UNIX boxes BITD

---

### Post by ActionParsnip on 2021-07-31
[https://serverfault.com/questions/147430/how-to-change-default-runlevel-of-ubuntu-lucid](https://serverfault.com/questions/147430/how-to-change-default-runlevel-of-ubuntu-lucid)

It's the same in newer releases

---

### Post by ActionParsnip on 2021-07-31
[https://linuxconfig.org/how-to-check-and-change-a-default-runlevel-on-ubuntu-linux](https://linuxconfig.org/how-to-check-and-change-a-default-runlevel-on-ubuntu-linux)

---

### Post by fausto99 on 2021-07-31
The only file in my /etc/init/ directory is a file called whoopsie.conf 
It seems to contain stuff about system crashes.

---

### Post by Holger_Gehrke on 2021-07-31
Since current Ubuntu releases use systemd shouldn't systemctl be the tool of choice ? 
According to the manual page for systemctl 'set-default' sets the default target to boot to, so 
```

systemctl set-default multi-user.target

```
should get you a fully functional command line system as the default.

Holger

---

