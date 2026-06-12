---
title: "[SOLVED] HELP!! terminal is dead and i cant use bash commands"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by satanic-yobbo on 2008-06-02
i ran the update manager and it came up with 110 updates which it then proceeded to install but came back with an error about installing bash and now i cannot use my terminal at all it has become completely unresponsive as if i am typing into a word processor or the like ..... 

what can i do to fix it that doesnt require code in terminal ?? 

can anyone help me ?? ......

please....

---

### Post by sayakb on 2008-06-02
Open Synaptic and navigate to Bash package. Right click on it and select "Mark for Reinstallation"
Press the Apply button, and then try again.

---

### Post by unutbu on 2008-06-02
Edit: LinuxIsInnovation's method is better.

Boot from a LiveCD. Open a terminal. (You can do this because the LiveCD has its own /bin/bash).

Mount your hard drive:
```
mkdir /Ubuntu
mount /dev/**sda1** /Ubuntu
```

You might have to **change sda1** to whatever your Ubuntu partition is called. If you do not know, type

```
fdisk -l
```
That should give you some clue as to which Linux filesystem is your Ubuntu partition. 

Now copy the LiveCD's version of bash to your Ubuntu partition's bash:

```
cp /bin/bash /Ubuntu/bin/bash
```

This is a stop-gap measure to get your system working again. You'll want to re-install bash from packages later.

---

### Post by satanic-yobbo on 2008-06-02
ok followed linux's advice and this is what i got 

E: bash: subprocess post-installation script killed by signal (Segmentation fault)

details are 

setting up bash (3.2-0ubuntu018)
dpkg error processing bash (--configue)
subprocess post installation script killed by signal(segmentation fault)
errors were encountered while processing:
bash
E: sub-process /usr/bin/dpkg retuned error code (1)
a package failed to install. trying to recover:

thats where it ended 
should i try the live cd ?

---

### Post by durand on 2008-06-02
Youch! Sounds kinda bad. Try this: Press Alt + F2, then type **gksudo nautilus** and when it loads, go to  /var/lib/dpkg/info/ and **move** (not copy) the bash.postinst file to a safe location. Then retry the above steps. If it doesn't work, move the file back before changing anything else.

---

### Post by Bablefish on 2008-06-02
In other words you might have to reinstall your OS

---

### Post by durand on 2008-06-02
It would be a hell of a lot easier to reinstall :(
or you can use the live cd, chroot into your install and run some update commands. It might work..

Mount your partition as unutbu suggested.

> Mount your hard drive:
Code:
mkdir /Ubuntu
mount /dev/sda1 /Ubuntu
You might have to change sda1 to whatever your Ubuntu partition is called. If you do not know, type

Code:
fdisk -l
That should give you some clue as to which Linux filesystem is your Ubuntu partition.

Then...
```

sudo chroot /Ubuntu
sudo aptitude update
sudo aptitude upgrade
exit

```
That should hopefully fix it

---

### Post by satanic-yobbo on 2008-06-03
after a heck of a lot of mucking around in files and transferring files and things i finnally decided that due to the fact that i didnt have anything more than a few songs on here that were already backed up from a previous re-install i just did a fresh install which took less time than i spent trying to fix the installed os anyway lol 

cheers to everyone for the help and advice anyway but i couldnt get it to work for me and i lost patience and re-installed it fresh

---

