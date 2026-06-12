---
title: "[SOLVED] Delete everything a package installed"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by phil90 on 2008-05-27
Hello

I would like to know if there is a way else than deleting everything manually to delete every file and folders a packages installed?


I thought that is what purge do but I found out it leaves quite a lot of files and folders.

Thank you

---

### Post by EXCiD3 on 2008-05-27
Using "Completely Remove" in synaptic or purging the package deletes anything included with the package and configuration files. This is as best as you can get, and depending on the package, some things may be left behind. What package were you having trouble with?

---

### Post by Butthead on 2008-05-28
Try running (without quotes) "sudo apt-get autoremove" in terminal.

That usually cleans out a lot of orphaned crap for me.

---

### Post by phil90 on 2008-05-29
Thank you  EXCiD3

I  have realized that removing packages does not delete everything when I remove my Wine and purged it. I watned to delete everything about the wine to reinstall it but the files were still there before I reinstall it. I had to manually delete .wine folder



Thank you Butthead 

but apt-get autoremove only removes the dependencies that were installed by the packages.

What I meant are the files that are left after a packages has been removed and purged.

---

### Post by EXCiD3 on 2008-05-29
Got it fix i take it? Good to hear! Yeah when purging or completely removing a package it only removes the files created during installation, meaning no configuration files (which will almost always just be located in your home folder like you found the .wine directory). If you want something to reinstall with the original settings, just delete its config folder and you should be back to where you started. :)

---

### Post by Butthead on 2008-05-29
Hmm, learned something new myself. 8-[

Now to go back and check the status on everythin I un-installed so far. ](*,)

---

### Post by EXCiD3 on 2008-05-30
> **Butthead said:**
> Hmm, learned something new myself. 8-[

Now to go back and check the status on everythin I un-installed so far. ](*,)

Haha, yeah if you dont plan on reinstalling your old apps i wouldnt worry about it too much since the config files are usually very small. Never know when you will learn something new trolling the forums here! :)

---

### Post by disturbedite on 2008-05-30
from command line,
```
sudo dpkg purge packagename
```will do the trick.

---

### Post by phil90 on 2008-05-30
Thank you 


I was not sure if there was another way than just doing it manually


Disturbedite , Would that not just do the same than using APT to remove the packages , the dependencies and purge the packages which does not delete all the files?

---

### Post by EXCiD3 on 2008-05-30
> **phil90 said:**
> Thank you 


I was not sure if there was another way than just doing it manually


Disturbedite , Would that not just do the same than using APT to remove the packages , the dependencies and purge the packages which does not delete all the files?

You are correct, this is no different than doing the same with apt-get or synaptic. It will just remove the packages like they do.

---

### Post by steveneddy on 2008-05-30
> **disturbedite said:**
> from command line,
```
sudo dpkg purge packagename
```will do the trick.

I haven't seen you around in ages.

Where have you been? 

Some kind of crazy adventure?

---

### Post by disturbedite on 2008-05-30
> **steveneddy said:**
> I haven't seen you around in ages.

Where have you been? 

Some kind of crazy adventure?
Yes!  a crazy adventure that is chronicled online here:
[http://ubuntuforums.org/showthread.php?t=809837](http://ubuntuforums.org/showthread.php?t=809837)

---

### Post by steveneddy on 2008-05-30
> **disturbedite said:**
> Yes!  a crazy adventure that is chronicled online here:
[http://ubuntuforums.org/showthread.php?t=809837](http://ubuntuforums.org/showthread.php?t=809837)

KDE! What are you? Nuts?!

:D

---

### Post by disturbedite on 2008-05-31
> **steveneddy said:**
> KDE! What are you? Nuts?!

:D
if not wanting a DE that restricts options is nuts, then, why yes i am!

(my sig does include kubuntu, btw)...

---

