---
title: "how to become super user before running a GUI ?"
date: 2008-05-26
forum: Programming Talk
---

### Post by brijith on 2008-05-26
Hai,

I have developed an application in python. It is to be ran with Super User privilege. What I do now to run it is open a terminal then become super user using the command **SU** then run my application in terminal. In debian and Ubuntu I have seen a pop up window asking root password will rise before any privileged windows like ***networks*** or ***Synaptic.*** How can I use that type of authentication. How can I raise that pop up window and become super user start  my application with super user

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by LaRoza on 2008-05-26
> **brijith said:**
> Hai,

I have developed an application in python. It is to be ran with Super User privilege. What I do now to run it is open a terminal then become super user using the command **SU** then run my application in terminal. In debian and Ubuntu I have seen a pop up window asking root password will rise before any privileged windows like ***networks*** or ***Synaptic.*** How can I use that type of authentication. How can I raise that pop up window and become super user start  my application with super user

**[COLOR="Red"]Thanks[/COLOR]**

Look into "man gksu".

---

### Post by xlinuks on 2008-05-26
Thus, if you wish, say, to run nautilus as a root/super-user press Alt+F2 to get the "Run Application" dialog, and type "gksudo nautilus" - you'll get prompted for the password, and if typed the correct password, nautilus will run as root.

---

### Post by brijith on 2008-05-27
**[COLOR="Red"]Thanks Friends[/COLOR]**

---

