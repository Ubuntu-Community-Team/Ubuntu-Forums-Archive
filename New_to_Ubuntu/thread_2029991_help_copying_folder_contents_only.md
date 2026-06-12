---
title: "help copying folder contents only"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-07-20
i know this is a reaaaally noob question but how can i copy the contents of a folder without copying the folder itself? here's what i have so far:
```
sudo cp -a /wubi/ /media/ubuntu/

```this gives me a folder called wubi inside /media/ubuntu/. i just want the contents of wubi. any ideas?

---

### Post by ubudog on 2012-07-20
Hi there, try this:

```
sudo cp -a /wubi/* /media/ubuntu/
```
Note: Remove the slash in front of 'wubi' if the directory wubi is in your working directory.  Having the slash will copy from /wubi, as opposed to /home/example/example/wubi.

Hope that helps!

---

### Post by z3nhakr on 2012-07-20
thanks :D

---

### Post by sudodus on 2012-07-20
```
sudo cp -a /wubi/* /media/ubuntu/
``` would work except for hidden files.

You can use a simple script file like this
```
#! /bin/bash

echo simple backup script using cp -auv SOURCE[directory]... DESTINATION_directory
echo cp -auv $*
echo press {ENTER} to continue or {CtrlC} to quit
read
cp -auv $*

```
so that you can see what will be copied before you actually run the command.

But when you get more used to linux, I suggest that you start using ```
rsync
``` for such tasks. Read ```
man rsync
``` to learn more about backing up or synchronizing directories.

---

### Post by z3nhakr on 2012-07-20
so which would be best for migrating my installation?

---

### Post by sudodus on 2012-07-20
> **z3nhakr said:**
> so which would be best for migrating my installation?
Do you want to migrate to a normal installation with dual boot?

Read this link [[COLOR="Red"]_https://help.ubuntu.com/community/MigrateWubi_[/COLOR]]("https://help.ubuntu.com/community/MigrateWubi")

---

### Post by z3nhakr on 2012-07-20
thanks. actually google led me right to that page a few minutes after i made that post. it's all good now :D

---

