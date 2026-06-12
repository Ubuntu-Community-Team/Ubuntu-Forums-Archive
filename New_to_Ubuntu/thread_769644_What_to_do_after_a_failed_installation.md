---
title: "What to do after a failed installation?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-26
When I tried to install Limewire the installation failed and after that I could not install anything and ultimately gave up and reformatted the hard drive.

Are there any suggestions on how to handle failed installations?

---

### Post by red_Marvin on 2008-04-26
When asking for help it is important to supply enough information. In this case; how did you try to install it? Limewire is not in the repos afaik. And also, how are you unable to install anything else? Did synaptic stop working? What are the error messages?

Good luck in the future :)

---

### Post by saskatchewan on 2008-04-26
Here is one of the error messages:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

---

### Post by NeoLithium on 2008-04-26
Ah, that happens sometimes with the package manager, when you get messages like that you simply need to run what it tells you:
```
sudo dpkg --configure -a
```
It will reinstall the package that broke during the installation and make everything all good once again :)

---

### Post by red_Marvin on 2008-04-26
have you tried running *sudo dpkg --configure -a* ?
EDIT: Gah ninja'd.

---

### Post by saskatchewan on 2008-04-26
I did but I just eneded up with more error messages.  Unfortunately I dont have those error messages handy since I am reformatting right now and resorting to using a Winblows computer.

---

