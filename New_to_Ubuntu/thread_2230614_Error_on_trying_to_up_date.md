---
title: "Error on trying to up date"
date: 2014-06-20
forum: New to Ubuntu
---

### Post by Rich42 on 2014-06-20
I would like some advice please running Ubuntu12.04

 Packard Bell   2.9GHz
 Name IMEDIA 1328
 Model Type  UTOW-SAM
 MSIOHQL No: SAN1058593
 S/No: 049652020726
 PID 0496520207P/No: PB34225201

The owner of the PC has not updated for many months!

So I did in terminal the following: sudo apt-get update

Them I tried to do an update in the normal way.

This did not work - error below.

Require installation of untrusted packets. 

python-lockfile

---

### Post by kira_belka2 on 2014-06-20
try > apt-get install python-lockfile

---

### Post by slickymaster on 2014-06-20
> **Rich42 said:**
> I would like some advice please running Ubuntu12.04

 Packard Bell   2.9GHz
 Name IMEDIA 1328
 Model Type  UTOW-SAM
 MSIOHQL No: SAN1058593
 S/No: 049652020726
 PID 0496520207P/No: PB34225201

The owner of the PC has not updated for many months!

So I did in terminal the following: sudo apt-get update

Them I tried to do an update in the normal way.

This did not work - error below.

Require installation of untrusted packets. 

python-lockfile

Can you please open a terminal window and run one at a time the following commands```
lsb_release -r && uname -a
sudo apt-get update && sudo apt-get upgrade
```And the post back here the output you get from each, using code tags for the effect.

---

