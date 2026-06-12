---
title: "Running gksu on boot???"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Skripka on 2008-08-18
I have an ATi card, that thanks to atipower, I'm able to overclock....BUT....

How do I get a gksu command to run on boot?  Or what would be the easiest way?


The terminal command I want to run on boot is

```

gksu atipower 3


```


I'm open to all methods-and considered a script, but writing that myself would be over my head at this point.

---

### Post by meanburrito920 on 2008-08-18
Ok, normally you DO NOT want to screw around with this if you don't know what you are doing, so make sure you back up all important information on your computer. You may want to check all this to make sure that this is absolutely correct, but basically you will be mucking around in some root folders. Sound fun? Once again, I dont know if this is the 'official' way to do things, but it *should* work.

So first, open yourself a root terminal and head over to /etc/init.d/

make yourself a new file called atipower.sh and stick the following text in it:
```

#!/bin/sh

atipower 3
exit 0

```

chmod a+x this.

then type the following code

```

update-rc.d atipower.sh defaults

```

to undo this if it screws up your system, use

```

update-rc.d atipower.sh remove

```

NOTE: Always keep notes of what you are changing when you mess with root stuff. Again, make sure you have your documents backed up before you do this.

---

### Post by lswb on 2008-08-18
Another, perhaps simpler way, is to add the line to the file /etc/rc.local (before the line that begins with "exit" of course!)

---

### Post by Skripka on 2008-08-18
Update:

Well I tried both you guys' ways (thx very much)

But they're not doing the trick (I'm stumped)-neither is getting atipower to cause the ati driver to (re)discover its other power modes [nothing happens, good or bad].

:confused:

---

### Post by lswb on 2008-08-18
I'm not familiar with the atipower command, but 2 things occur to me:

1) commands in rc.local (or in files in /etc/init.d) do not use gksu, gksudo, etc; These commands are already being run with root privledges. If you use sudo, gksudo, etc. in these files, the commands will fail since there is no one logged in yet who can enter a password anyway.


2) Does the atipower command require that X be running? If so, you may want to try Main Menu/System/Preferences/Session/Startup Programs and add the command there.

---

### Post by Skripka on 2008-08-18
> **lswb said:**
> I'm not familiar with the atipower command, but 2 things occur to me:

1) commands in rc.local (or in files in /etc/init.d) do not use gksu, gksudo, etc; These commands are already being run with root privledges. If you use sudo, gksudo, etc. in these files, the commands will fail since there is no one logged in yet who can enter a password anyway.


2) Does the atipower command require that X be running? If so, you may want to try Main Menu/System/Preferences/Session/Startup Programs and add the command there.


Excellent!

#2 solved it.

FYI-

Atipower looks at the card itself, and scans what power modes it has (which is the # following the atipower command)---in my case:

1) Default (5oo mHz core/600 mHz memory) 
2) Underclocked by ~100mHz on core, default memory clock 
3) Overclocked (~650mHz core/~775mHz memory)

The reason for dicking around this way being the poorly written ATi drivers only have the default setting on the clocks (and the driver GUI control is a VERY stripped down-only allows gamma, antialiasing, and ansitropic filtering settings---no control over the clocks as with their windows driver).  The hardware has the modes built in--ATi just chooses not to allow you to change it with their driver.


thx vdeddy much!

---

