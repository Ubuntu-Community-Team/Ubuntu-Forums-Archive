---
title: "Avant  Window Navigator Question"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by seamustry on 2008-05-06
Is there a way to make avant window navigator just a dock for launchers?

Right now, it has launchers and it also shows what programs are running but I don't want to see those in the dock. How can I change that?

---

### Post by glennric on 2008-05-06
This can't be done yet, but the developers are working on it.  See the following blueprint:
[https://blueprints.launchpad.net/awn/+spec/allow-launcher-only]("https://blueprints.launchpad.net/awn/+spec/allow-launcher-only")

---

### Post by aktiwers on 2008-05-06
Go to System => Preferences => AWM Manager

and pick "Applets".

Then remove "Launcher/Taskmanager"

If its not there (the manager I mean) install it first:
```
sudo apt-get install awn-manager
```

Edit: seams to work here?

---

### Post by glennric on 2008-05-06
> **aktiwers said:**
> Go to System => Preferences => AWM Manager

and pick "Applets".

Then remove "Launcher/Taskmanager"

If its not there (the manager I mean) install it first:
```
sudo apt-get install awn-manager
```

Edit: seams to work here?

If he does that he won't have launchers either though.  He wants just launchers, and not the task manager.

---

### Post by aktiwers on 2008-05-06
You are right, sorry.. just tested it. 
I just remember I did this though? Maybe there are separate plugins for those two then.

I really think I had this on my old install of avant.

---

### Post by glennric on 2008-05-06
> **aktiwers said:**
> You are right, sorry.. just tested it. 
I just remember I did this though? Maybe there are separate plugins for those two then.

I really think I had this on my old install of avant.

The standalone launcher is being developed and is in the bzr repository, but it doesn't work very well yet.  There is also a simple launcher that I think is for individual applications.  I don't think these are in the version of awn-extras-applets in the repository.  I have been running my own compilation from the bzr source for so long that I don't know any more.

---

### Post by seamustry on 2008-05-07
aah ok thanks for all the help...i guess i'll just wait

---

### Post by moonbeam on 2008-05-07
> **glennric said:**
> The standalone launcher is being developed and is in the bzr repository, but it doesn't work very well yet.  There is also a simple launcher that I think is for individual applications.  I don't think these are in the version of awn-extras-applets in the repository.  I have been running my own compilation from the bzr source for so long that I don't know any more.

They're available in the awn-testing ppa but not reacocard's ppa.

---

