---
title: "[SOLVED] wine install problem"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2008-11-01
Hi, I just downloaded wine from advice on another thread. The download seemed to complete properly, but the package installer says "Dependency is not satisfiable:libasound2" Can anyone tell me what this means? I should add that I'm pretty new to all this so a simple explanation would be great. Thanks.

---

### Post by Bodsda on 2008-11-01
The 'Dependency not satisfiable' suggests that wine (when installed) had trouble installing some other things that it needs, luckily it tells us what it needs, try typing this into a terminal {Applications--> Accessories--> Terminal}

```
sudo apt-get install libasound2
```

Copy and paste any errors here if you get them, if not then wine should work fine. 

Bodsda

---

### Post by Dermot Doyle on 2008-11-01
Am I right in thinking this is ok? Can't say I fully understand it, but there don't seem to be any errors.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono-cairo2.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by gandaran on 2008-11-01
why don't you install wine from the repos?
code:
sudo apt-get install wine

---

### Post by Dermot Doyle on 2008-11-01
Because I didn't know I could. As I said, I'm new to this, but thanks it all seems to have worked and wine has appeared in my applications. 
There seem to be a confusion (to a non-techy) of ways to do the same thing and I never really understand the pros and cons of why people suggest different solutions. But I'm learning.
Thanks again.

---

### Post by gandaran on 2008-11-01
the best way to install and remove applications is to use synaptic package manager, it has thousands of programs to choose from,you just mark the selected application for install or for complete removal and click the apply button.
any time you try to install something first check if the application is in synaptic

---

