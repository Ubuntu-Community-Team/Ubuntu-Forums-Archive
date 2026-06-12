---
title: "Alpha2 &quot;application problem&quot; messages"
date: 2011-07-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-25
Hello,

Today's update brought the following problems or nuisance.  As soon as I login and do a routine "sudo aptitude update && sudo aptitude safe-upgrade", the screen shows:

1.  Application problem. Sorry, Gnome-Settings Daemon closed unexpectedly...

2. Sorry, the program "zeitgeist-daemon " closed unexpectedly...

3.  Sorry, the program "unity_support_test" closed unexpectedly..

I remember reporting "zeitgeist-daemon" problem several days ago.

I can still do the updating.  Any suggestions?

:confused:

---

### Post by cariboo on 2011-07-25
Just ignore the messages, or add your **me too** to the bug report, the errors which are normal during a testing phase, won't stop you from updating, or using your system.

---

### Post by jbicha on 2011-07-26
Apport (which provides those pop-up crash messages) is only enabled by default during the development cycle. Edit /etc/default/apport to enable or disable them completely. 1 is on; 0 is off.

---

### Post by ubrox on 2011-07-26
me too. same problem

---

### Post by iClouseau88 on 2011-07-26
PROBLEM SOLVED:

```

sudo gedit /etc/default/apport

```

Changed enabled=1 to enabled=0

Save file and exit

Thank you, jbicha!

:D

---

