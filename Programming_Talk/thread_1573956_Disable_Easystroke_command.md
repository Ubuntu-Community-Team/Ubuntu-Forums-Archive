---
title: "Disable Easystroke command"
date: 2010-09-13
forum: Programming Talk
---

### Post by hariks0 on 2010-09-13
Does anybody know if Easystroke could be disabled/enabled from command line. A status toggle or 'Start disabled' option will also do.

Thanks in advance.

---

### Post by hariks0 on 2010-09-16
Bump.

---

### Post by stinkeye on 2010-09-16
In your easystroke preferences you can choose to display a tray icon
which gives you a right click disable option.

---

### Post by hariks0 on 2010-09-16
That is what I am doing at present. What I want is an option to start it disbled, so that I will not have to disable after every login and just enable from the tray icon. Other wise I will have to remove it from startup and invoke it manually whenever required.

The reason is, I am using Button1 for easystrokes.

---

### Post by hariks0 on 2010-10-31
Bump.

---

### Post by ragtag on 2010-10-31
I'm not sure you can do this in an easy way, without digging into the source of easystroke. The man page for easystroke gives no option for starting it disabled from the command line.

What you can do is set up a gesture for disabling easystroke. Just pick Type>Misc, and choose Disable (Enable) from the menu. This is quicker than clicking the icon.  Of course, once disabled, you cant use the gesture to re-enable it. :)

Maybe someone else has a better solution.

---

### Post by hariks0 on 2010-10-31
Thank you so much. It almost serves my requirement. A solution as per the Original post is welcome, though.

:popcorn:

---

### Post by semidark on 2011-05-01
there is a solution. You can trigger easystroke actions via the bash.

So add an action that ist called toggle_active that disables or enables easystroke.

In bash:

easystroke send  toggle_active

Done ;)

---

### Post by hariks0 on 2011-05-02
A script file with the following content did not work

```
#!/bin/bash
easystroke send toggle_active
```

Can you please provide the correct method for doing this?

TIA.

---

### Post by hariks0 on 2011-05-04
Bump !

---

### Post by hariks0 on 2011-05-16
A script file [as per this post]("http://ubuntuforums.org/showthread.php?p=10768664#post10768664") with the following content did not work

Code:

#!/bin/bash
easystroke send toggle_active

What I want is  master gesture to enable/disable Easystroke. Once it is disabled, it should listen for occurrence of the master gesture alone.

Can you guys please provide the correct method for doing this?

TIA.

---

### Post by cariboo on 2011-05-16
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by hariks0 on 2011-05-21
Bump !

---

### Post by hariks0 on 2011-05-30
Bump again ! :(

---

### Post by Enterpart on 2011-09-01
how about this

```
killall easystroke; xte 'sleep 5'; easystroke
```

you would need xautomation

```
sudo apt-get install xautomation
```

it will close easystroke and open it in 5 seconds, or you can change to any delay you want

---

### Post by MadCow108 on 2011-09-01
> **hariks0 said:**
> Bump again ! :(

apparently nobody knows of a built in solution.
So scratch your own itch!
get the source and add the feature yourself
If you are unfamiliar with the programming language, see it as an opportunity to learn.

---

