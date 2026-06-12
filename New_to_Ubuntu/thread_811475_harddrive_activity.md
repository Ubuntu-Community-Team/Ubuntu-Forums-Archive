---
title: "harddrive activity"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by abraxas334 on 2008-05-29
I have noticed that after booting my system into gutsy for about 20 minutes after booting there is a lot of harddrive activity going on (longer than usual) is there any chance of finding out why the computer is accessing the harddrive and what exactly it is doing, as the system monitor will give me no detail about this.
Cheers for the help.

---

### Post by kpkeerthi on 2008-05-29
Do you have Tracker running in the background? It a search tool included in ubuntu and it may be busy indexing your files.

Check with:
```
ps aux | grep tracker
```

You may disable it from starting from System -> Preferences -> Session -> Startup Programs

---

### Post by abraxas334 on 2008-05-29
thanks that might indeed be the problem, tho i guess there is no program or other means to find out, what exactly the harddrive is doing?

---

### Post by sdennie on 2008-05-29
If that happens to not be the problem, you could also try this: [http://ubuntuforums.org/showpost.php?p=5066042&postcount=2](http://ubuntuforums.org/showpost.php?p=5066042&postcount=2)

---

### Post by AndyCooll on 2008-05-29
You can also check via the System Monitor. 
System > Administration > System Monitor ...IIRC, I'm not actually at my Linux box at the moment.

:cool:

---

