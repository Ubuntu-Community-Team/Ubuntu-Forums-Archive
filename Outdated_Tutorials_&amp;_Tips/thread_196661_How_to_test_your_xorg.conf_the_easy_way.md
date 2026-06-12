---
title: "How to test your xorg.conf the easy way"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by pjbgravely on 2006-06-14
I have read many howtos on hot to setup special xorg.conf's. They all have different ways to edit and test the file. Some go as far as having you kill gdm and doing everything in a raw console. I found an easy way to edit and test in a howto ( can't remember where) and thought I would share it.

First back up you xorg.conf using command line or GUI. When you are ready to test your new one simply:

Ctrl / Alt / F2  ( push all three at the same time.)

Login, and then type:

xinit -- :2

If everything is right you should see a Grey desktop, and X for the mouse cursor and a term window. You can test glxinfo in the term if direct rendering is what you are working on. Then hit Ctrl / Alt / Backspace to kill the Xwindow.

If all you get are errors don't worry.

Either way, to get back to your running desktop hit: Ctrl / Alt / F7

If you didn't kill the Grey Xwindow you will find it again by hitting Ctrl / Alt / F8

Now you can check the log to see what happened under /var/log/Xorg.2.log.

Doing it this way lets you test without losing your present desktop, which is a great help if you are searching the web for a solution and need to test every trick you find. This also works for dual screen testing.

Paul

---

### Post by Greeface on 2006-07-02
Ah, I will have to use the method next time I am playing with my xorg.conf, having to restart it everytime gets pretty tedious (especially when you suck at editing it :D ).

---

### Post by tomchuk on 2006-07-02
You can also start another server using Xnest, and you don't even have to leave X:
```

sudo apt-get install xnest
Xnest :1 -geometry 320x240

```

---

### Post by Hairy_Palms on 2006-07-03
or even better
> gdmflexiserver --xnest
brings another desktop inside your desktop vmware style :)

---

### Post by motin on 2008-01-26
I just wrote a Howto and a helping bash+zenity script for these purposes: [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

---

