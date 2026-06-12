---
title: "s3 Prosavage KN133 drivers... help needed"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by cthorpey on 2008-09-02
Hi, 
I am new to xubuntu and to be honest i am struggling,
I am trying to resurrect an old Sharp GP10 laptop.
I installed Xubuntu and it recognised the lan and wlan, I have done all the updates and the system is fantastic.
I still have the problem of the graphics card driver.
I cannot set the resolution to anything above 800 x 600.
I have worked my way through the solutions that came up on a google search but they seem to be a bit out of date.
Any help would be greatly appreciated
Many Thanks
Chris

---

### Post by aimpau on 2008-09-02
1. check if the videocard is propriety
    Applications>>>System>>Hardware drivers

2. if not, open a terminal and
```

gksu displayconfig-gtk

```

3. try to save your settings by clicking the floppy disk on displayconfig-gtk.

---

### Post by russu52 on 2009-01-18
i have the same problem - i installed xubuntu 8.10 on an amd 1.25 ghz and it has an agp s3 card. do u think this command will do the trick? thanks

---

### Post by Yoodle on 2009-02-09
> **russu52 said:**
> i have the same problem - i installed xubuntu 8.10 on an amd 1.25 ghz and it has an agp s3 card. do u think this command will do the trick? thanks

Unfortunately, I tried the command and it didn't do anything for me.  Didn't even bring up the app.  A minimized app appears for me that says "Starting Administrative" but then it just goes away.

I've found that the monitor seems to make a big difference in what resolutions Ubuntu is able to display.  I thought it would be more a function of the video card, but I've tried different monitors on a machine and got different results.  The monitor I'm on now won't go above 1024x768, but if I boot into Windows, I can get higher resolutions with the same machine/monitor.

Doesn't make sense to me, maybe someone else can explain?

---

