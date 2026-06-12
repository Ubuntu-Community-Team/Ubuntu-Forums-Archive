---
title: "Install gone horrably wrong"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by mrtornado on 2008-05-02
Ok I was trying to install btnx so I could use my side buttons on my mouse and I uninstalled libgtk2.0-0 somehow. So then I reinstalled it but when I rebooted my computer I go strait to the command line instead of my login screen and when i typed firefox this came up **GTK- WARNING**: cannot open display**. Can anyone help me restore my computer to how it was before when I could use the log in screen. Or help me fix my problem.

---

### Post by mrtornado on 2008-05-02
please someone help

---

### Post by ecs_pf5 on 2008-05-02
I'm a n00b so treat this suggestion with caution but you could try doing a forum search on the command:

sudo dpkg reconfigure xserver-xorg

it's a guess that it might help :confused:

or maybe just type

startx 

& see what happens

---

### Post by schauerlich on 2008-05-02
Run this command:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

You might need to answer a few questions. Then run:

```

sudo startx

```

---

### Post by mrtornado on 2008-05-03
ok so thanks to you guys i am able to use programs through the konsole now but when i uninstalled the file i mentioned in the first post i think it might of uninstalled others how do i find out what those are so i can install them and make my computer go back to normal.

---

### Post by ecs_pf5 on 2008-05-03
Are you still getting **GTK- WARNING**: cannot open display**.

If so maybe have a look at:

message #613 & #614 on page:

[]("http://ubuntuforums.org/showthread.php?t=241868&page=64")[http://ubuntuforums.org/showthread.php?t=241868&page=62](http://ubuntuforums.org/showthread.php?t=241868&page=62)

again, it's a guess, you might want to wait for other's comments ;)

-?-

---

