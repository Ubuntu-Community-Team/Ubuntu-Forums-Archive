---
title: "Only one software management tool is allowed?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-26
Hi

When ever I try to install something I get the message that only one software management tool is allowed and to please close the others.

How do I close the others?

---

### Post by axor1337 on 2008-04-26
please give more details are you using add/remove or terminal to install or is it a app that is not in the repositories  is ubuntu updating ate the same time ?

---

### Post by Technoviking on 2008-04-26
Do you have a terminal with apt-get or dpkg running, or maybe you started the Synaptic GUI and minimized it.

---

### Post by axor1337 on 2008-04-26
well i guess you figured it out on your own im me if you need more help

---

### Post by saskatchewan on 2008-04-26
My Ububu won't let me install anything.

I mean plugins, skype, limewire...

Anything!!!

---

### Post by dangerpl on 2008-04-26
What exactly happens? Does it stop at 15/24?

---

### Post by tamoneya on 2008-04-26
what have you tried in an attempt to install these program.  What was the result of the actions specifically.

---

### Post by ad_267 on 2008-04-26
How are you trying to install these? What errors are you getting?

---

### Post by saskatchewan on 2008-04-26
> **axor1337 said:**
> well i guess you figured it out on your own im me if you need more help
Sorry that I missed you, I am back trying again.  I am trying to install Limewire, Skype and RealPlayer (not all at the same time).  I have been trying to do this by using Gdebi package installer

---

### Post by hums07 on 2008-04-26
Probably something went wrong when Gdebi tried to install a package. It should've given you a message. Probably you can try this on the terminal:
```
sudo apt-get update
```
and see what message it gives.

---

### Post by saskatchewan on 2008-04-26
> **dangerpl said:**
> What exactly happens? Does it stop at 15/24?
When I try to install pugins I get the message 
E:dpkg was interrupted, you must manually run ' dpkg -- configure -a' to correct the problem.
e: cache->open()failed, please report.

I dont know how to either manually run dpkg or report.

---

### Post by ad_267 on 2008-04-26
Go to Applications - Accessories - Terminal and type in 
```
dpkg -- configure -a
```

If you get an error about not having the required permissions then try:
```
sudo dpkg -- configure -a
```

---

### Post by SunnyRabbiera on 2008-04-26
you have to make sure that apt or another package manager is not running by going into the system monitor by going up to "system" then to "administration" and then "system monitor"
if you tried running gdebi and add/remove at the same time no wonder why you had issues.

---

