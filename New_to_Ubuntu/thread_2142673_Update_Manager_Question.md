---
title: "Update Manager Question"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by UncleAsriel on 2013-05-06
I'm currently running the Update manager, getting all the lasted drivers and other such goodness to keep my system up-to-date. However, I've had some problems in the past when I insall all updates at once- it can ruin the graphics configuration, ruin wireless configurations, and other such nasty things.

I would like to try installing each update individually, so I can determine which individual updates are causing the problems. However, the GUI method (Update Manager) has no "Select All/Deselect all" option. Is there some function I can to to get the GUI to work the way I want it to? Or can I do this throught the command line (and if so, how?)?

My command-line fu is still very weak, and while I aim to improve it, I want to be sure what I'm doing is proper (and I can undo it without having to wipe the drive clean and re-installing - my current solution to goofs).

What can you wonderful folks advise?

---

### Post by deadflowr on 2013-05-06
Aren't you getting checkmark boxes next to the packages being updated in the update manager?


There is also usually a details dropdown at the bottom that will show you what archiac changes are being made to whichever package is highlighted.

---

### Post by ibjsb4 on 2013-05-06
Command-line fu is not necessary to have complete control of your update downloads.  [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Synaptic+Package+Manager&sa=Search&cof=FORID:9") will do that.

```
sudo apt-get install synaptic
```

---

### Post by UncleAsriel on 2013-05-06
> **deadflowr said:**
> Aren't you getting checkmark boxes next to the packages being updated in the update manager?

There is also usually a details dropdown at the bottom that will show you what archiac changes are being made to whichever package is highlighted.

I get individual checkmark boxes, but when there are 147 updates waiting, it can be a pain to uncheck them all individually.

Also, given my newbie nature, I won't pretend to know the impacts of each individual install based on the stats in the details. I suppose I could Google all of the details, though. I just figured trying each install in a bit-by-bit basis would be a Good Idea.


> **ibjsb4 said:**
> Command-line fu is not necessary to have complete control of your update downloads.  [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Synaptic+Package+Manager&sa=Search&cof=FORID:9") will do that.

```
sudo apt-get install synaptic
```


Ah, thank you!

That's what I was hoping for! I'm installing it as we speak.

To uninstall uyndesired software, I just use 

```
sudo apt-get remove PROGRAM_NAME
```

I just need to know the program name. On the Update Manager, I see a listing of the package's names - is there a way to convert that to a text doccument, so I can have that information on a separate machine in case I screw up my main machine and have to remove it via command line?

---

### Post by ibjsb4 on 2013-05-06
If I understand you correctly, you want a backup of all packages installed.  That is done in synaptic with a markings list.  Up in the synaptic tool bar, go to File>Save Markings As.  Also check the box for a complete system save.

To restore if necessary, File>Read Markings.

---

### Post by UncleAsriel on 2013-05-06
Thank you, ibjsb4!

What I wanted was a listing of the package names. As I install each package one-by-one (paying attention to each one I add), I know I always run the risk of install something not compatible with my cantankerous NVIDIA graphics card. 

As I install each package, I want to have something to consult (either a sheet of paper or a document on another computer) with the names of all drivers I have to installed up to this point. This way, if I do something ruinous, I can always reboot the machine, go to the terminal then remove the package name via  ```
sudo apt-get remove PACKAGE-NAME
``` 

I know that in order to target a package i want to remove, I need its name. Being able to have this list exist somewhere other than the main drive I'm working on.

I realize this is an inelegant solution, but given my limited knowledge base, it seems like the most effective method. Is there another way I can do this (such as installing all updates at once, then - in the case of errors - go to the command line and look for where the problems are through some command-line magic?)?

---

### Post by Cheesemill on 2013-05-06
The problem with your method is that updating your system doesn't usually install any extra packages, it just updates the packages that are already installed.

For example if updating python breaks your system then your solution would be to simply uninstall the python package. Not only would this not take you back to your pre-update state but removing python would also trigger the removal of all of its dependant packages which would uninstall nearly your entire system.

I find that the best method for installing updates is just to go ahead and install all of them. Maybe I've just been lucky but I've never had an issue with updates breaking the system (except when I'm running the development version of Ubuntu).

---

### Post by ibjsb4 on 2013-05-06
> What I wanted was a listing of the package names.

```
dpkg --get-selections > ~/my-packages
```

Then look in your home folder for "my-packages".

also

[http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html](http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html)

---

### Post by UncleAsriel on 2013-05-06
> **Cheesemill said:**
> The problem with your method is that updating your system doesn't usually install any extra packages, it just updates the packages that are already installed.

For example if updating python breaks your system then your solution would be to simply uninstall the python package. Not only would this not take you back to your pre-update state but removing python would also trigger the removal of all of its dependant packages which would uninstall nearly your entire system.

I find that the best method for installing updates is just to go ahead and install all of them. Maybe I've just been lucky but I've never had an issue with updates breaking the system (except when I'm running the development version of Ubuntu).


Shows how much I know. I thought that updating packages simply involved throwing out all of the old stuff and replacing it with a new, complete package. 

I'm seriously considering your approach and just installing the whole 147 packages at once, but I'm still waffling.

> **ibjsb4 said:**
> ```
dpkg --get-selections > ~/my-packages
```

Then look in your home folder for "my-packages".

also

[http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html](http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html)

Ah! This is most helpful.


During all of the installations, I keep getting problems with the capiutils package. This makes me slightly annoyed - while I know it's mostly for[ ISDN cards ]("https://launchpad.net/ubuntu/precise/+package/capiutils")(which I'm not currently using), I have a suspicion that this could bite me in the backside down the line (if, for instance, I eventually start using a wired connection for internet, could this become a problem?)

Am I over-thinking this, or is this a legitimate concern?

---

### Post by UncleAsriel on 2013-05-06
Well, crap. After my interface froze (and bringing up the terminal by pressing Ctrl + Alt + F2 proved useless - the username and password led to my login being denied, even though I entered the same password I use for sudo commands - and yes, I know about entering things into the password field here doesn't show characters), I had to hard reboot my system to get access to it. 

I checked [the original methods]("http://ubuntuforums.org/showthread.php?t=2140063") I used to get the wireless working, but the blacklisted entries appear to be in place. I am attempting to reinstall the linux drivers from the proprietor's website as we speak.

I will share the new netinfo.txt in a few minutes if this does not work.

---

### Post by UncleAsriel on 2013-05-06
null

---

### Post by UncleAsriel on 2013-05-07
Thanks for your help, everyone! I managed to get the update system working thanks to you all. I appreciate the aid!

---

