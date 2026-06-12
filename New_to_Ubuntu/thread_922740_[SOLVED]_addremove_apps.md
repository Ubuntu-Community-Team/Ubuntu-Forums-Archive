---
title: "[SOLVED] add/remove apps"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Dan 2.0 on 2008-09-17
Hi all, 

Background: I have just installed Ubuntu for the first time. When running the update manager the laptop froze. I restarted the laptop without the update finishing. Now i have these errors and when i click on update manager to try and finish it nothing happens. 

When go to applications in the top panel and click on add/remove i get the little waiting mouse icon and the 'starting add/remove...' in the bottom panel. After 5 secs this then disappears and nothing happens. 

I've tried using the synaptic package manager as an alternative but when opening encounter this error: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried running 'dpkg --configure -a' but it brings up this error:

danny@danny-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

I'm using the user account that I set up with the installation. I thought this has Administrator privilages?

Sorry for the length. Tried to be detailed. Any ideas how to fix this? LOL

---

### Post by InfinityCircuit on 2008-09-17
```
sudo dpkg --configure -a
```

---

### Post by OffAxis on 2008-09-17
```
sudo dpkg --configure -a
```

edit: you're fast InfinityCircuit.

---

### Post by drs305 on 2008-09-17
You need to run it as root:
```
sudo dpkg --configure -a
```

Enter your password, you won't see it but it will register. Hit enter after you have typed it in.

---

### Post by karlr42 on 2008-09-17
> **Dan 2.0 said:**
> 
I'm using the user account that I set up with the installation. I thought this has Administrator privileges
Nope, it doesn't. It has* permission to get Administrator privileges for a little while* by using sudo, but only then. That way, you know that if you need to use sudo, this command is probably something potentially dangerous.

---

### Post by Dan 2.0 on 2008-09-17
Hey all, 

Instantly solved. Wow that was fast! :)

Thanks!

---

### Post by Paqman on 2008-09-17
> **Dan 2.0 said:**
> 
I'm using the user account that I set up with the installation. I thought this has Administrator privilages?


It does. Admin rights give you the ability to execute commands with sudo (or gksudo/kdesu for graphical applications)

[Lots of info about sudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Sef on 2008-09-17
>  I'm using the user account that I set up with the installation. I thought this has Administrator privilages? You are.  Your system just had a hiccup.

>  Sorry for the length. Tried to be detailed. Any ideas how to fix this? LOL     It was well written.  Better to be detailed than not.

---

