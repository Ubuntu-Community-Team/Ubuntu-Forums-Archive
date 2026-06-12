---
title: "Dropbox start at startup"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by thorbs on 2012-04-16
Hi I installed dropbox on my lenovo t61, Lubuntu. At the moment I have to run it in terminal, but I would like to start it up automatically at startup. How to do this?

---

### Post by Rodney9 on 2012-04-16
See - [How_I_can_autostart_a_program_when_logging_into_Desktop]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_I_can_autostart_a_program_when_logging_into_Desktop")


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by thorbs on 2012-04-18
I actually did search the ubuntu one stop thread first, though without luck. Find i hard to use.

---

### Post by kc1di on 2012-04-18
> **thorbs said:**
> I actually did search the ubuntu one stop thread first, though without luck. Find i hard to use.

Was your Question answered?
If so please mark the thread as Solved.
:)

---

### Post by cortman on 2012-04-18
It's pretty simple. In a terminal enter

```
gksu leafpad /etc/xdg/lxsession/Lubuntu/autostart
```

Ad the line

```
@dropbox
```

Save and restart. You should be good to go!

---

### Post by thorbs on 2012-04-20
Thanks that was easy

---

