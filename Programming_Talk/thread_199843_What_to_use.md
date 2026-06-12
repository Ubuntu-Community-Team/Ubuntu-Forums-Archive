---
title: "What to use ???"
date: 2006-06-19
forum: Programming Talk
---

### Post by SteffJay on 2006-06-19
Hello everyone. Its a good chance that somebody can help me out here. There are two problems to overcome (then i will be a happy bunny !!). Firstly: the firewall (firestarter) i installed using my usual login account (not root), it runs ok. Unfortunately, every time i reboot, i have to start it manually and use my password for me to start it with. That is not good. There is also the Macromedia Flash Server that i want to start at bootup as well. I have tried **/etc/init.d/fms start** (which is the starting sequence) in **systems/prefs/sessions/startup programs** but it will not auto start. The second problem is: I need to run a DC Hub Server on this box but cannot find one that i can use (preferably with a GUI). Any info with the above will be greatly received.

---

### Post by meng on 2006-06-19
You don't need to run firestarter every time you boot, only if you want to change the configuration of your firewall (iptables).

---

### Post by SteffJay on 2006-06-19
Hello **Meng**. Everytime i check it when i reboot,  it is'nt running and i  have to start it.  :confused:

---

### Post by meng on 2006-06-19
No seriously, firestarter only modifies iptables. If it's not running, the firewall is still intact.

---

### Post by SteffJay on 2006-06-19
Is there a way i can check instead of running it ?

---

### Post by meng on 2006-06-19
What do you want to check? I don't understand the question. If you want a log of attempted intrusions, firestarter will give you that only if you run it. Alternatively, if you want to try hacking into your box from another station ... Do you mean something different?

Myself, I just happen to know that the firewall is up and that's good enough for me.

---

### Post by SteffJay on 2006-06-19
All i want to know is, how can i check if the firewall is actually running !!

---

### Post by Revert on 2006-06-19
Here's a [thread ]("http://www.ubuntuforums.org/showthread.php?t=177738&highlight=firestarter+boot")explaining how to start up Firestarter automatically with a password.

Like meng said, though, you don't need to.  Firestarter's just a simple GUI to modify IP tables.  

To test it, why not try some port scanners?  See if it's actually blocking stuff.

---

### Post by meng on 2006-06-19
[QUOTE=SteffJay]All i want to know is, how can i check if the firewall is actually running !![/QUOTE]
Unless you take active steps to stop the firewall, it is running. That's how you know.

Unlike Windows firewalls, there doesn't need to be a program/icon visible in order for the security measures to be enabled. I wonder if you are stuck in this mindset.

---

### Post by SteffJay on 2006-06-19
Ok. Thanks to **Meng** & **Revert's** advice  I went here [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and tested everything and i am happy that the firewall is doing its job !!!!  :p  So, any more help with the DC Hub Server and the 2 x autoboots anyone ???

---

