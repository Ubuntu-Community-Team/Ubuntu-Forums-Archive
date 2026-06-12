---
title: "Synaptic Package Manager Complete Removal Function"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by toady2 on 2013-08-31
Does the complete removal function in Synaptic Package Manager also remove any dependencies that the main program called in? 

Thanks.

---

### Post by Jonathan Precise on 2013-08-31
No, it does not remove dependencies (you have to do that manually). The complete removal removes the program's configuration files. This is similar to:

```
sudo apt-get remove ***--purge*** **_application-name_**
```

replacing application-name with the name of the app (--purge removes the config files).

---

### Post by toady2 on 2013-08-31
Is there a way to find out which extra dependencies the program called in (not the ones that are already on my system)? I tried searching that program again in the package manger and when the installation window comes up no dependencies are listed. I also tried checking the properties of that program that clicking on the dependencies tab and it listed a lot of dependencies but it doesn't have any date (installed date) associated with it so I'm clueless as to what to remove because I don't want to remove dependencies existed there previously before that program called it. By the way the program i'm talking about here is midori. 

Thanks

---

### Post by Dennis N on 2013-08-31
you can remove dependencies that are no longer needed by other programs:

from the man page of apt-get:
> autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.

autoremove is an option with apt-get:

[B]sudo apt-get autoremove
[/B]
Also can be done with Synaptic. Click the Status button, and choose "installed (auto removable)". Those can be selected and marked for removal.

---

### Post by toady2 on 2013-08-31
Hi I looked around the web about the command sudo apt-get autoremove and I see some people had issues after doing it? Issues where they can't log in and where system files being deleted? So i'm a bit scared to try that command. Did you have any experience with that command?

---

### Post by Dennis N on 2013-08-31
Only a few times. You can run a simulation which will show you what would happen:

Run autoremove in simulation mode:

```
apt-get -s autoremove
```

no sudo is necessary with a simulation (-s option). It will tell you what packages would be removed. If you decide to go ahead, run

```
sudo apt-get autoremove
```

---

### Post by toady2 on 2013-08-31
Hey thanks so much for that -s option! Oh man that would come handy in so many situations. 
I tried it and it only showed three dependencies so I'm not even gonna bother with removing anything.

---

### Post by Dennis N on 2013-08-31
If you are concerned, I would say that since we have so much disk space now, leaving the dependencies installed has little downside. Generally, they are not big files anyway.

---

### Post by toady2 on 2013-08-31
I was concerned but now that i know it's only three I don't mind. I go crazy when things are cluttered and there're things that I don't need any more. Real world and in the virtual world. 
I'll just leave them installed. I have 123GB left anyways. 
Thanks for your time.

---

### Post by vasa1 on 2013-08-31
I've been using *sudo apt-get autoremove* since I started using Ubuntu with 11.04. I haven't noticed any ill-effect.

One request: when you post something like "I see some people had issues after doing it", please do share a few links if possible.

---

### Post by toady2 on 2013-08-31
Thanks for sharing your experience.
I'll remember to share some links next time.

---

### Post by Jonathan Precise on 2013-09-01
No problem!:) Please mark this thread as solved by going to thread tools and clicking "Mark as solved"

---

