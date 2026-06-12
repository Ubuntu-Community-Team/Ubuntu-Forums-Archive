---
title: "Just launch application in unix script"
date: 2010-07-21
forum: Programming Talk
---

### Post by hakermania on 2010-07-21
OK, let;s say that in a part of my script I want to launch to applications and then the script continue to the next line after launching the applications. For example,
```
vlc & gedit
echo "Vlc and gedit launched" > $HOME/apps.log
```
The problem is that the applications do launch, but they must exit to continue writing to apps.log file. Is there any way to just launch an application and then continue?

---

### Post by iponeverything on 2010-07-21
```

vlc& 
disown
gedit&
disown
echo "Vlc and gedit launched" > $HOME/apps.log

```

---

### Post by trent.josephsen on 2010-07-21
I HAIL YOU!

Wow, what a simple solution.  It's a wonder I didn't notice that before.  Will certainly come in handy.

---

### Post by hakermania on 2010-07-22
Cool thank you very much. :)

---

