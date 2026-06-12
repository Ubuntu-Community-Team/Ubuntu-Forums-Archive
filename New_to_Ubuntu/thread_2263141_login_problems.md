---
title: "login problems"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by earthbryan on 2015-01-29
I was updating and when I rebooted seemed to have lost gnome desktop and only have ubuntu 14.10 login page with my desktop name but my password does not work have not changed the password what next step

---

### Post by Bashing-om on 2015-01-29
earthbryan; Hi ! Welcome to the forum.

> **earthbryan said:**
> I was updating and when I rebooted seemed to have lost gnome desktop and only have ubuntu 14.10 login page with my desktop name but my password does not work have not changed the password what next step

That next step is to see if "you" have authority to access X:
From that login screen, key combo ctl+alt+F1 to gain a console. 
Issue terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority

```
It should be "you" as the group and owner:
as in:
> 
sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Aug  1 10:10 .Xauthority

where I am "sysop" .

Next is who owns /home ?
```

ls -al /home
ls -al /home/earthbryan

``` where "earthbryan' is the username on the system.

Maybe as simple as this.

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

