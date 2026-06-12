---
title: "Pavucontrol for Audacity"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by Elborath on 2013-01-28
Hi everybody. I am not only new to this forum but I am totally new to Linux! And pretty new to writing commands in terminal windows! But not completely computer illiterate! I have installed Audacity in Ubuntu and now want to install Pavucontrol. I have downloaded the pkg but when I try to install it get the message: Items cannot be installed or removed until the pkg catalogue is repaired. Do you want to repair it now? I click 'Repair' but nothing happens. I just keep getting the message which appears now when I try to install other pkgs. Help??

Elborath

---

### Post by Bucky Ball on 2013-01-28
Welcome to the forums. You need to have Pulse Audio installed, which it should be by default. Why not just install pavucontrol from Software Centre or Synaptics? You don't need to add any repos. It's there already.

---

### Post by furything on 2013-01-28
Try repairing package installer through terminal
```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Elborath on 2013-01-28
Thank both Bucky and Furything. I did as you advised Fury--the repository couldn't be found (accessed or whatever) even though I had ?installed it and downloaded Audacity through it. So some info was missing--it couldn't find 'a' for example. Yes Bucky, according to Software Centre I DO have Pavucontrol installed already! Told you I was a noobie! However I can't seem to open it in order to change the settings so I can record streaming (I need to record voice in an online virtual environment). 

I still get the error message (repair needed) when I open Software centre :(

---

### Post by Elborath on 2013-01-28
These are the details regarding the failure:

installArchives() failed: dpkg: dependency problems prevent configuration of pavucontrol:
 libpulse0 (1:1.1-0ubuntu15.2) breaks pavucontrol (<< 0.9.8) and is installed.
  Version of pavucontrol to be configured is 0.9.5-1ubuntu1.
dpkg: error processing pavucontrol (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 pavucontrol
Error in function:
dpkg: dependency problems prevent configuration of pavucontrol:
 libpulse0 (1:1.1-0ubuntu15.2) breaks pavucontrol (<< 0.9.8) and is installed.
  Version of pavucontrol to be configured is 0.9.5-1ubuntu1.
dpkg: error processing pavucontrol (--configure):
 dependency problems - leaving unconfigured

---

### Post by furything on 2013-01-28
Looks a bit messy 
I think you need to clean up first by removing pavucontrol
```
sudo dpkg --force-all -P pavucontrol
```
Redo previous commands from earlier post to ensure all ok

Use the packager manager tool and install the software you want through it.

If you don't like the default tool then tell it to install synaptic package manager and use that instead.

You may have to tell it to use 3rd party repositories (that depends on where the software is that you  want to install).

---

### Post by GordThompson on 2013-01-28
I just tried installing 'pavucontrol' from the official repositories via Synaptic Package Manager and it worked fine for me. I'm on Ubuntu 12.04 LTS and it installed

pavucontrol 0.99.2-1build1

I notice that your version of pavucontrol is older (0.9.5-1ubuntu1). Are you running an older version of Ubuntu?

---

### Post by Elborath on 2013-01-28
Thanks guys for all your help. followed your instructions to the letter Furything and it worked just great. Error messages gone and pavucontrol installed perfectly from Software Centre. I'm running 12.04 Gord. My friend who urged me to try Linux advised against 12.10 for some reason I forget. 

Very new to this but your help has been truly appreciated and I'm a quick learner. No doubt I'll be asking again--I'm thinking of installing Mint on my other laptop...

---

### Post by furything on 2013-01-29
Your welcome.
Glad you are now sorted.

---

