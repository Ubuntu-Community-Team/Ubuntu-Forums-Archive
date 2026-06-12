---
title: "Can I remove/disable apt-xapian-index in Kubuntu?"
date: 2018-06-22
forum: New to Ubuntu
---

### Post by eldklot on 2018-06-22
Hello everyone,

I have noticed that every time I try to update my system or install something using Muon, the apt-xapian-index will run for several minutes taking up to 100% of the CPU capacity bringing the system to a halt. I thought of removing it but I realized that some other packages will be removed with it:
```
[FONT=monospace][COLOR=#000000]sudo apt purge apt-xapian-index --simulate[/COLOR]  
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  apt-xapian-index* kubuntu-driver-manager* kubuntu-notification-helper* muon*[/FONT]
```

So I decided not to. Then I thought, in order to prevent it from running, to rename the /usr/share/apt-xapian-index to something else.
I appreciate if you could tell me if there is a way of removing it without removing the other packages or if renaming it will actually stop it from running.
In either case, will that affect the ability of the system to update or install new software in a negative way?

Thanks in advance!

eldklot

---

