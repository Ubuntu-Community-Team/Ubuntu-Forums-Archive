---
title: "Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by Silent Messy Death on 2011-10-01
Hey i keep running intothis error  (Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied))
when ever i try installing jre so i can play minecraft would like to kno if any one could help me with it thx.

---

### Post by jon zendatta on 2011-10-01
You have either another application open. Update Manager, Synaptic or Terminal

---

### Post by nitstorm on 2011-10-01
*sorry for the misinformation I accidentally provided*

---

### Post by matt_symes on 2011-10-01
Hi

> **nitstorm said:**
> To add to jon zendatta's answer, 

You have another application that is running under sudo or gksudo, that is super-user permission. Only one application can be executed with super-user privileges at a time. So you will have to wait for that application to stop/end before another application can be executed with super-user privileges.

You can know which programs run with Super-user privileges as when they need to be run with super-user privileges, they will prompt you for your password.

Sorry nitstorm bu this is simply not true. You can have many applications, daemons and scripts running as root at the same time.

You can only install one program at a time though as the dpkg lock file gets locked. The lock file is used as concurrency control for dpkg and is used by dpkg and so indirectly by apt, aptitude, software center, synaptic and update manager (etc). 

Kind regards.

---

### Post by nitstorm on 2011-10-01
> **matt_symes said:**
> Hi



Sorry nitstorm bu this is simply not true. You can have many applications, daemons and scripts running as root at the same time.

You can only install one program at a time though as the dpkg lock file gets locked. The lock file is used as concurrency control for dpkg and is used by dpkg and so indirectly by apt, aptitude, software center, synaptic and update manager (etc). 

Kind regards.

Extremely sorry and thanks for catching me there. I know that, and yet don't know what I was thinking when I made that error. Will edit the post. Thanks again and extreme apologies to everyone.

---

### Post by drs305 on 2011-10-01
You should be able to remove the lock by closing the package management apps as mentioned earlier.

If you can't find any GUI apps running, you can try closing them via the command line but a safer way is to simply log off and reboot. During a normal shutdown, the apps should close in an orderly fashion and remove the lock. It should be removed after rebooting.

If rebooting doesn't remove the lock, you can see which apps you have currently running with admin privileges with:
```
ps -u root
```
You can then try killing the app with:
```
sudo killall <appname> # Example: sudo killall synapic
```

---

### Post by Silent Messy Death on 2011-10-01
xD omg i feel so stupid didnt put sudo infront of 
apt-get install sun-java6-jdk sun-java6-jre

thanks for help help guys

---

### Post by drs305 on 2011-10-01
:-)  

Hadn't even thought of that - nor ever seen it mentioned as a solution. We've all done similar things.

If you wouldn't mind, please mark this SOLVED using the 'Thread Tools' link near the top right of the original post.

---

### Post by jebbushell on 2013-04-09
I got this by running:

 [B]sudo apt-get update && apt-get upgrade.

[/B]The fix in my case was to separate the statements:
[B]
sudo apt-get update
sudo apt-get upgrade

[/B]My guess is that somehow these guys got into a deadly embrace.

---

### Post by wildmanne39 on 2013-04-09
Thread closed. Please do not post in old threads.

---

