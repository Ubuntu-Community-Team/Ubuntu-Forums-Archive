---
title: "Error updating packages"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Sundance on 2008-09-09
When I click on the icon for the package manager and click to update the packages I get this message:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What does it mean and what do I need to do?

Thanks

---

### Post by iaculallad on 2008-09-09
> **Sundance said:**
> When I click on the icon for the package manager and click to update the packages I get this message:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What does it mean and what do I need to do?

Thanks

On your terminal, just add the sudo command:

```
sudo dpkg --configure -a
```

---

### Post by Sundance on 2008-09-10
Thanks, that solved that problem but there seems to be more. First it took like 3 or 4 tried to download all the files. It kept stopping the download and would give me a message it was reading and then do nothing. I finally did get all the packages downloads and started the install. But, I get a broken package message, telling me to use the broken filter program. What is a broken package? I click OK and it either starts the install and the system freezes or it gives me an error something about Alien Arena. I have tried to remove Alien Arena as I do not play games but it will not allow me to do so.

How did this get so screwed up, it's a new os install, any ideas. What happened to ease to use never crashes linux?

Thanks,

Steve

---

### Post by jemate18 on 2008-09-10
> **Sundance said:**
> Thanks, that solved that problem but there seems to be more. First it took like 3 or 4 tried to download all the files. It kept stopping the download and would give me a message it was reading and then do nothing. I finally did get all the packages downloads and started the install. But, I get a broken package message, telling me to use the broken filter program. What is a broken package? I click OK and it either starts the install and the system freezes or it gives me an error something about Alien Arena. I have tried to remove Alien Arena as I do not play games but it will not allow me to do so.

How did this get so screwed up, it's a new os install, any ideas. What happened to ease to use never crashes linux?

Thanks,

Steve

do you get any errors for running
> sudo apt-get update
in the terminal?

---

### Post by iaculallad on 2008-09-10
Try reading this Ubuntu Community [HowTo]("https://help.ubuntu.com/community/SynapticHowto") on Synaptics Package Manager.

---

