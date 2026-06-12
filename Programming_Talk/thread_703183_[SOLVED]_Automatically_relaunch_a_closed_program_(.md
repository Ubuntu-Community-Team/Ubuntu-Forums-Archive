---
title: "[SOLVED] Automatically relaunch a closed program (in KDE)"
date: 2008-02-21
forum: Programming Talk
---

### Post by russell-ault on 2008-02-21
This may be the wrong forum, so I'll apologize in advance, but I've got what I hope to be a fairly simple question. I have been poking around computers for a decade (but always in the wrong places), so please bear with my ignorance here.

Basically, all I'm looking for (and can't find) is a simple script (or something) that will automatically relaunch/restart a program that has been closed. For instance, say I want Kontact to always be open, and someone closes it; I'd like it to relaunch itself automatically. Ideally the script would be fairly generic so that it will work with different programs. If it makes a difference I'll be using KDE, and if you really want to make my month, I'm looking for something that will not only reload the program, but reload it in the same workspace as it was before it was closed.

Again, sorry for my utter lack of experience (when I was younger I foolishly wasted my time learning Flash instead of something like C or Python, which I should have learned), and rest assured that I will learn from every comment left! :)

---

### Post by Jussi Kukkonen on 2008-02-21
No need for C, just a bit of shell script:

```
#!/bin/sh

while (true) do
    program_you_want_to_run
done

```

Lots of ways to make that more professional, but that should get you started... Save that somewhere (I use *~/bin/* for stuff like this), make it executable (*chmod +x*) and add a launcher that starts the script to your panel (or even edit the menu item for the program if you want to).

---

### Post by jsmiith on 2008-02-21
Heres a simple bash script I just threw together(using gaim as an example)


```
#!/bin/sh
while [ 1 ]
do
 if ! ps -e | grep gaim
 then
 gaim
 fi
sleep 2
done
```

---

### Post by russell-ault on 2008-02-21
Wow, thanks for the quick response, guys! Between this and a few other things I've been trying to pick up as much as I can on scripting and syntax, and this is sure a big help!

--edit--

Actually Jussi, just tried yours out, and while it sounds like a good idea, all it does is open an instance of program_you_want_to_run as quickly as it can (on instance at a time), instead of only if closed.

---

