---
title: "Updating everything?"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by josh17 on 2013-08-21
I was told that after installing Ubuntu I need to do something specific in order to have all drivers and such updated and working properly, but I was not told what this something is, does anyone know what I need to do, and if so how I do it? I'd really like to have Ubuntu running to it's full potential :D

---

### Post by Cheesemill on 2013-08-21
Just run the Update Manager to make sure your system is fully updated, you can launch it by opening the dash and searching for 'update'.

---

### Post by slickymaster on 2013-08-21
Perhaps who told you was referring to the common update procedure, which you can do by opening a terminal window and running the following commands:```
sudo apt-get update
sudo apt-get dist-upgrade
```you'll be prompted for your password to proceed, so just type it in.

What this commands do is: the first **apt-get update** is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the location(s) specified in /etc/apt/sources.list and the second **apt-get dist-upgrade** in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages.

---

### Post by grahammechanical on 2013-08-21
When you installed Ubuntu did you confirm that you wanted updates to be installed at the same time? Then the finished installation would have been up to date.

Did you also choose to install Third Party Software? Then a proprietary video driver would also have been installed. Some hardware works better with a proprietary video driver than with the Open source video driver called Nouveau. I personally find Nouveau to be sufficient.

I cannot think of anything else we need to do to get Ubuntu running at its full potential. It all depends upon the hardware and how new it is and whether there are proprietary drivers available to make full use of the hardware.

Regards.

---

### Post by josh17 on 2013-08-21
> **grahammechanical said:**
> When you installed Ubuntu did you confirm that you wanted updates to be installed at the same time? Then the finished installation would have been up to date.

Did you also choose to install Third Party Software? Then a proprietary video driver would also have been installed. Some hardware works better with a proprietary video driver than with the Open source video driver called Nouveau. I personally find Nouveau to be sufficient.

I cannot think of anything else we need to do to get Ubuntu running at its full potential. It all depends upon the hardware and how new it is and whether there are proprietary drivers available to make full use of the hardware.

Regards.

I don't remember if I did all that, it's been a while since I've used Ubuntu but I've had it installed for nearly a year, I used the update manager last night though, so everything should be good to go?

---

### Post by deadflowr on 2013-08-21
> **josh17 said:**
> I don't remember if I did all that, it's been a while since I've used Ubuntu but I've had it installed for nearly a year, I used the update manager last night though, so everything should be good to go?

You should be updated, pretty much.
If you want to make sure you're system is truly up-to-date, if running 12.04(which has Update manager, as opposed to 12.10 and newer which has Software Updater) open Update manager and click check, which'll check for new updates, if any are available.
From 12.10 on, Software Updater automatically checks for updates when launched.

---

### Post by craig10x on 2013-08-21
And if you type in "software and updates" into the dash search and bring that up, and then go to the updates tab, you can set it to check for updates daily (i think by default they might have it set to check weekly)...
Once you set it for daily, everyday you boot up ubuntu it will check and bring up the updates within about 30 minutes of you getting on the internet (assuming there are any of course)...you will see the software updater icon in you unity bar when it pops up...

Of course, you can also run the Software Updater manually at any time as well by clicking it on from the dash search ;)

---

