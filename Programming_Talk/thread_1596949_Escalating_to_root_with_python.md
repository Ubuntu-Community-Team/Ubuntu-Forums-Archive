---
title: "Escalating to root with python?"
date: 2010-10-14
forum: Programming Talk
---

### Post by tgm4883 on 2010-10-14
I have a python program that includes a GUI. What I want to do is check if running as root, if not running as root then escalate to root priveledges. So far, the code below seems to work, i'm just not sure if that is the best way.

My question is, is this the best way to escalate to root privileges? I can't just rely on someone to run it from a terminal with sudo as someone might doubleclick the .py file. 


```
    if not os.geteuid()==0: ## Check if running as root
        if not os.isatty(0):  ## If not running in a terminal
            os.system("gksudo savfl-sst.py") # script is restarted, now as root
        else:  ## If we are in a terminal
            sys.exit("\nPlease run this utility as root\n")
```

:EDIT:

I just wanted to add that doing an os.system that runs the same py (this code is from savfl-sst.py) without stopping the original process just feels wrong.

---

### Post by ssam on 2010-10-15
probably best to use gksu instead of gksudo. it will auto detect if su or sudo should be used.

you could use one these instead of os.system
[http://docs.python.org/library/os.html#os.execl](http://docs.python.org/library/os.html#os.execl)

also instead of checking os.isatty(), why not try to run gksu and then print the message if that fails.

```

try:
    os.execv("gksu", "savfl-sst.py")
except OSError:
    sys.exit("\nPlease run this utility as root\n")

```

you could also replace
"savfl-sst.py"
with
os.path.realpath(__file__)
incase the script gets renamed.

---

### Post by nvteighen on 2010-10-15
Ugh...

I guess you want to do something like some GNOME applications that allow root escalation without restarting the program... like the "Date & Time" configuration application.

IIRC, this kind of stuff is done via Kerberos or another authentication library... I'm not sure which is it. Anyway, restarting the same application opening a subshell looks really bad, IMO.

---

### Post by ssam on 2010-10-15
i think they use policykit. it lets you do all sorts of clever things. eg allow none root users to do specific tasks, under specific conditions.

[http://ubuntuforums.org/showthread.php?t=1359397](http://ubuntuforums.org/showthread.php?t=1359397) might help if you want to go that route

---

### Post by nvteighen on 2010-10-15
> **ssam said:**
> i think they use policykit. it lets you do all sorts of clever things. eg allow none root users to do specific tasks, under specific conditions.


Yup, that is the library. Thanks for refreshing my memory!... :P

---

