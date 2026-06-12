---
title: "Reading package lists... Done???"
date: 2016-02-23
forum: New to Ubuntu
---

### Post by frank72 on 2016-02-23
Hello all,
I hope someone can help. with multiple fresh linux installs I'm getting

Reading package lists... Done

when trying sudo apt-get update.

I know its not getting updates because the popup update window installed a bunch?
 please let me know if you need more info, its a fresh 14.04 on ! pc and an older 14.04 in the other room.
Am I getting hacked before i can do my first update? All i can think of.

Thanx in advance

EDIT: ADDED:   No warnings by the way
Sorry belongs in updates section. My bad.

AGAIN:

---

### Post by Bashing-om on 2016-02-23
frank72; Hello;

The command " sudo apt-get update " syncs your system database with that of the mirror that you are using .
```

sysop@1404mini:~$ sudo apt-get update
<snip>
Ign http://ubuntu.osuosl.org trusty/multiverse Translation-en_US
Ign http://ubuntu.osuosl.org trusty/restricted Translation-en_US
Ign http://ubuntu.osuosl.org trusty/universe Translation-en_US
Fetched 3,925 kB in 6s (643 kB/s)                                              
Reading package lists... Done
sysop@1404mini:~$

```
once the sync operations complete, now one can do the actual update of installed softwares.
As:
```

sudo apt-get upgrade

```
"upgrade" will not install new packages ( as in a new kernel ) for that to happen a different command:
```

sudo apt-get dist-upgrade

```


Now to complicate the matter ... 'apt-get' is presently being superseded by 'apt' . 'apt' is enhanced and has added features.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by frank72 on 2016-02-23
Lol Thanx man. I feel allitle dumb...

---

### Post by Bashing-om on 2016-02-23
frank72; Hey ...

Like, I have been at this for longer than I care to think about ... and I still have more than my share of "those" moments ->
where do I go from here .

it's a learning curve
[INDENT][INDENT][INDENT]we are all at some point on that curve
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-02-23
Software Updater not only updates the package lists but also downloads & installs the updated packages. One operation for the user. Two operations for the Software Updater utility.

---

### Post by Bucky Ball on 2016-02-23
> **frank72 said:**
> Lol Thanx man. I feel allitle dumb...

Welcome. You should actually feel a little smarter. You learned something today and most of us, old and new users, do that every day here. Learning about what we don't know is part of the fun and part of what makes Ubuntu interesting, so no need to feel dumb. :D

Please see the first link in my signature to mark the thread as solved. See? You learned something else today! ;)

(PS: This thread is in the right place. ***Installations and Upgrades*** is for installs and upgrades of the OS release, not updates. :))

---

