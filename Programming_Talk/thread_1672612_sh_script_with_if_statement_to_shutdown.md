---
title: "sh script with if statement to shutdown"
date: 2011-01-21
forum: Programming Talk
---

### Post by Jonny87 on 2011-01-21
I have a script that I using to run some tasks such as back ups, I also want to have the comp turn itself on early in the morn and schedule the script to run at that time when no-one is using the comp.

I want to add a shutdown command to the end of the script so that it shuts down the comp when its done, however I don't want it to shut down if someone is logged on (or accessing a samba shared folder).

Is anyone able to give me an example of how this might be done if it is possible?

---

### Post by fct on 2011-01-21
This should give you the number of currently logged on users:

who | wc -l

---

### Post by luvshines on 2011-01-21
You may want to explore 'at' command
It has some interesting options.
I haven't used it myself, but looks like in your case it might be helpful

---

### Post by Jonny87 on 2011-01-22
> **fct said:**
> This should give you the number of currently logged on users:

who | wc -l

Any idea how would use that with the shutdown command in a script? I'm guessing that it would possibly be with an "if statement" but my I'm still learning scripts and not to familiar with the "if statement" as I've hardly use it. could you possibly give me an example?

---

### Post by hakermania on 2011-01-22
> **Jonny87 said:**
> Any idea how would use that with the shutdown command in a script? I'm guessing that it would possibly be with an "if statement" but my I'm still learning scripts and not to familiar with the "if statement" as I've hardly use it. could you possibly give me an example?
```
if [ $(who | wc -l) -eq 0 ]; then
#there is none user logged in, so proceed with shutdown :)
#for example dbus-send --print-reply --system --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
 mplampla
fi
```
Not-tested (this will work if he command "who" has no output if none user is logged in)

---

### Post by fct on 2011-01-22
> **Jonny87 said:**
> Any idea how would use that with the shutdown command in a script? I'm guessing that it would possibly be with an "if statement" but my I'm still learning scripts and not to familiar with the "if statement" as I've hardly use it. could you possibly give me an example?

Then you should read some tutorials. I suggest this one:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

