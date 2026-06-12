---
title: "KUBUNTU 16.04 Software manager does not install"
date: 2017-01-27
forum: New to Ubuntu
---

### Post by selahattin2 on 2017-01-27
When i try to use the software manager to update it wont
theres 248 updates and i cannot do anything it just stays frozen 
Please help ASAP

---

### Post by Perfect Storm on 2017-01-27
Try open the terminal/konsole (and close the manager) and:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by selahattin2 on 2017-01-27
I cant software manager useees apt-get and when its running you cant close it

---

### Post by Perfect Storm on 2017-01-27
you can't close software manager when running apt-get?

---

### Post by selahattin2 on 2017-01-27
It CANT be closed

---

### Post by selahattin2 on 2017-01-29
also managed to install the updates but...the software manager/store is plain empty i can only use the ubuntu software center.
bump

---

### Post by Geoffrey_Arndt on 2017-01-29
what is the specific KDE software manager you are trying to use (name & name of package . . . e.g., muon and/or apper or other?).   

Have you tried via command line to install synaptic package manager?

sudo apt install synaptic

BTW - - there is a CLI program called "xkill" . . . . suggest you install that to kill any open apps that are hung (but not to be the normal way to close a program . . . just for if nothing else works or for emergencies.)

BTW2 - - you cannot have more than 1 package manager open at the same time . . . one only.    Otherwise major problems.

---

