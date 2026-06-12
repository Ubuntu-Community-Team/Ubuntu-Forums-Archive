---
title: "Can not run the upgrade"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-04-17
```
Can not run the upgrade
This usually is caused by a system where /tmp is mounted noexec. Please remount without noexec and run the upgrade again.
ray@ray-Latitude-D630:~$ 
```
tks

just need the command to fix also if i run this command i also get the following error

```
root@ray-Latitude-D630:/home/ray# sudo rm -rf /tmp*
rm: cannot remove ‘/tmp’: Device or resource busy
root@ray-Latitude-D630:/home/ray#
```

---

### Post by holycow131415 on 2014-04-17
Did you google? First result: [http://askubuntu.com/questions/311438/how-to-make-tmp-executable](http://askubuntu.com/questions/311438/how-to-make-tmp-executable)

---

### Post by rburkartjo on 2014-04-17
holy yes i did but didnt find that happens sometimes. tks for the info that is exactly what i need to update to ubuntu 14.04

---

