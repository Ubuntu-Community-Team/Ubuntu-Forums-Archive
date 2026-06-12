---
title: "change login name"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by petegreenhorn on 2008-08-01
hi just wondered if it's possible to change my login name

---

### Post by bobnutfield on 2008-08-01
Type in your terminal:

> man usermod

It explains it all

---

### Post by drs305 on 2008-08-01
Edited: There are ways to do this without copying the home folder, so I'm going to defer to bobnutfield's advice...

---

### Post by Thelasko on 2008-08-01
[Yes, it is.]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by prshah on 2008-08-01
> **petegreenhorn said:**
> hi just wondered if it's possible to change my login name

You can change your username by booting into the recovery console, then giving the command
```

usermod -l newname -m -d /home/newname oldname

```
this will change your username from oldname to newname, create an appropriate home folder, and copy your files into the new home folder, and set permissions and ownerships accordingly.

You need to do this in the recovery console because usermod will not allow changes to the name of a logged-in user.

Note that this may still cause problems; eg. any cron jobs etc setup in the old username will not be migrated automatically.

In short, unless you have a compelling reason to change the name, don't do it.

---

### Post by diacad on 2011-11-24
prshah:  I would like to try this, but I do not know how to boot into the "recovery console".  Do you hit a special combination of keys while booting up or what?

---

### Post by haqking on 2011-11-24
> **diacad said:**
> prshah:  I would like to try this, but I do not know how to boot into the "recovery console".  Do you hit a special combination of keys while booting up or what?

i expect you will get moved to your own thread but you can do it by pressing shift if you have single mode.

if it is a dual boot then choose recovery from menu

---

### Post by nothingspecial on 2011-11-24
Please don't bump old threads to the top.

Make your own thread :)

Closed.

---

