---
title: "Dash very slow"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by madjr on 2011-09-05
on natty and up to alpha3 it was fast (no blur), but now is very slow and i think is the blur thing that the open drivers with my ATI x1250 dont support yet.

how could i go on disable it to test?

i cant find ccsm in the software center..

---

### Post by madjr on 2011-09-05
made bug report here if anyone else has same issue:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/841527](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/841527)

---

### Post by mc4man on 2011-09-05
```
sudo apt-get install compizconfig-settings-manager
```
You could try 'static blur' which is set the 1st time you open the dash in a session or no blur which is definitely overly transparent

Edit: here's a slightly older active blur performance bug that shows 'fix released', I guess not for all..
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890)

---

### Post by madjr on 2011-09-05
> **mc4man said:**
> ```
sudo apt-get install compizconfig-settings-manager
```
You could try 'static blur' which is set the 1st time you open the dash in a session or no blur which is definitely overly transparent

Edit: here's a slightly older active blur performance bug that shows 'fix released', I guess not for all..
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824890)

thanks i'll check that out

---

