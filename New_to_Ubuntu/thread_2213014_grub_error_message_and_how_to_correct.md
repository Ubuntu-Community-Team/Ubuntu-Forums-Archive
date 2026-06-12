---
title: "grub error message and how to correct"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-03-24
when i run the below command i get this error message

ray@ray-Latitude-D630:~$ !3122
sudo gedit /etc/default/grub 

** (gedit:6641): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-7dFwBfAcRu: Connection refused
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.

(gedit:6641): IBUS-WARNING **: The owner of /home/ray/.config/ibus/bus is not root!

note i can still edit grub and get my changes to be accepted. however how can i correct this error message. tks

---

### Post by rburkartjo on 2014-03-24
however if i run
ray@ray-Latitude-D630:~$ gksudo gedit /etc/default/grub
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.

i get no error message

---

