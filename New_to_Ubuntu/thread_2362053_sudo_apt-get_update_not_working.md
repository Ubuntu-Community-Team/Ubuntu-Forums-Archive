---
title: "sudo apt-get update not working"
date: 2017-05-23
forum: New to Ubuntu
---

### Post by adhdluke on 2017-05-23
When I run the command, I get this
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```
I was attempting to install Wine before this, but it wasn't going well.
I'm running Ubuntu 16.04 MATE 64-bit

---

### Post by LastDino on 2017-05-23
Are you entirely sure that there is no other installation process or uninstallation going on? 

Maybe package manager is running? Or you have other terminal open with the process going on?

This generally indicates that there is other process open which using this directory

---

### Post by adhdluke on 2017-05-23
How can I find out what process is using the directory?

---

### Post by QIII on 2017-05-23
It is being used by another instance of a package manager.  If you have a GUI one open, close it.  If one is running in a terminal, kill that.

---

### Post by adhdluke on 2017-05-23
I have no package manager GUI open, but how do I kill it if it's running in the background?
Under the "Software Boutique" I got the "Software" a while ago. Could that be causing it?

---

### Post by deadflowr on 2017-05-23
it's probably automatic updates running.
check software and updates, or software sources > updates: when there are security updates.

---

### Post by sp40140 on 2017-05-23
> **adhdluke said:**
> 
I was attempting to install Wine before this, but it wasn't going well.

From this line... I can suggest that you reboot your machine and try to update.

---

### Post by adhdluke on 2017-05-23
I rebooted, and it's fine now.

---

