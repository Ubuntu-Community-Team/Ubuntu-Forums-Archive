---
title: "update manager doesnt update"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by pierreyy on 2011-09-14
hey guys... some time ago an update on my pc was interupted several times and now the update manager gives me an error when i try to update... any suggestions?

this message comes up:

Failed to load the package list

This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.

the "details" dropbar says:

E:Could not open file /tmp/aptdaemon-frozen-statusMvXV07/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.






im running natty narwhal 11.04 on a toshiba a665

---

### Post by LowSky on 2011-09-14
open terminal

then open nautilus using sudo

```
gksu nautilus
```

go to /tmp folder

delete aptdaemon folder. (don't worry its a temp folder nothing will be harmed)

try doing an update from terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by pierreyy on 2011-09-15
hey!

 thank you lowsky!

 but the problem is still unresolved... what happens now is that update manager has downloaded the updates but as it is applying changes the manager freezes and i have to "pkill" the update manager from the terminal, i tried updating from the terminal and the terminal freezes at the same part the manager does.... is there any way i can delete the existing downloaded but not yet installed updates? if i do so, will i face problems retrying to update again? thank you!

---

### Post by fdrake on 2011-09-15
> **pierreyy said:**
> hey!

 thank you lowsky!

 but the problem is still unresolved... what happens now is that update manager has downloaded the updates but as it is applying changes the manager freezes and i have to "pkill" the update manager from the terminal, i tried updating from the terminal and the terminal freezes at the same part the manager does.... is there any way i can delete the existing downloaded but not yet installed updates? if i do so, will i face problems retrying to update again? thank you!
try:
```

sudo aptitude clean && sudo aptitude autoclean
sudo aptitude -f update && sudo aptitude -f upgrade

```

---

### Post by pierreyy on 2011-09-15
thank you fdrake 


 the "clean" command was helpfull... the other however resulted in a problem

>   E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?  


 btw yes i am root... thanks in advance!

---

### Post by drs305 on 2011-09-15
Those messages indicate that there are multiple processes trying to access APT. Often the user will have left Synaptic open while also trying updates from the terminal.

If Synaptic is open, close it. If you have any other GUI package manager open close it. 

If you still get the lock message, the safest thing is to reboot, as any open processes should be shut down in an orderly fashion and the lock should be removed.

---

### Post by fdrake on 2011-09-15
> **drs305 said:**
> those messages indicate that there are multiple processes trying to access apt. Often the user will have left synaptic open while also trying updates from the terminal.

If synaptic is open, close it. If you have any other gui package manager open close it. 

If you still get the lock message, the safest thing is to reboot, as any open processes should be shut down in an orderly fashion and the lock should be removed.

+1

---

### Post by pierreyy on 2011-09-15
thank you so much! *marking as solved*

---

