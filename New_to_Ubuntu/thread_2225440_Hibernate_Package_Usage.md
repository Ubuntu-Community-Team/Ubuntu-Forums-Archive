---
title: "Hibernate Package Usage"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by DGINSD on 2014-05-21
So there's a package in the Ubuntu repo named  hibernate which is basically a set of scripts that goes through the 3 methods of hibernation available to Linux the method that works for my machine is uswsusp but it only works perfectly when run via 
```
sudo hibernate
```
which runs the script from the hibernate package.  So I've added the file to /etc/polki-1/logins or what ever it is to get the hibernate option to show up, it does and it works but doesn't execute hibernate via the hibernate package scripts.

With all the changes to ubuntu and how hibernate is run finding correct accurate info has been near impossible. So hopefully someone else can help, how do I make the hibernate menu entry execute the hibernate command (script) rather than what ever other method it's using now?

---

### Post by DGINSD on 2014-05-26
Ok so a bit more detail...
 

 Hibernate works perfectly with all three methods available; kernel, uswsusp, and tuxonice, but all three methods leave screen brightness controls inoperative, an annoyance more than a deal breaker, but mentioning it out of completeness, and the bigger problem, networking no longer works, not wifi and not plugging in a ethernet cable.  
 

 Nothing I've tried after resume will seem to bring it back up not unloading and reloading modules, pressing the wifi power button (which doesn't work ever anyway), I've tried not using the propritary driver (which wouldn't explain wired networking not working) all with the same result.
 

 The issue is kinda intermitent when I use the combination of calling uswsusp through the hibernation script but I haven't seemed to find any reason why. Log files have been rather unhelpful the hibernation process seems to work perfectly in all methods according to the log files.

---

