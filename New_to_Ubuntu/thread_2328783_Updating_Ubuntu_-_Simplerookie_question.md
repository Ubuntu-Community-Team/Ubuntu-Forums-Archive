---
title: "Updating Ubuntu - Simple/rookie question"
date: 2016-06-24
forum: New to Ubuntu
---

### Post by UtnubuLap on 2016-06-24
Hey!

Every few days I update Ubuntu via running "Software Updater", at least that is what I though.

I just did so, and then I opened "Ubuntu Software". There are 3 updates there which did not get downloaded via "Software Updater".

Why is this the case? Why split updates to two places? Is there one way to update everything, instead of checking out two places?

The updates are: "OS Updates", "Archive Manager" and "Software & Updates".

Thank for any help!

---

### Post by grahammechanical on 2016-06-24
There has always been more than one way to update the system. 

If you select About this computer you will get System Settings at the Details page and that will have a small panel at the bottom right that will say "Checking for Update." This kind of multiplication is for our convenience.

Linux distributions are made up of many software packages from many software projects. Each package depends on other packages. And those packages may not necessarily be from the same software project. So, when one package has been upgraded it is usually the case that other dependent packages will also need to be upgraded as well.

Then these upgrade packages have to be put into the update channels/repositories. They are put in individually, Humans have to do this. So, it is often the case that packages are held back from being installed until the dependencies are also available.

You will see this in Software Updater. Packages will be listed but they will not be ticked for download. It just so happens the Ubuntu Software is showing these held back packages as available updates. Whereas, Software Updater is not designed to notify us of updates to held back packages.

Regards.

---

### Post by UtnubuLap on 2016-06-24
Thanks for clarifying the process, but I'm still puzzled, and still left wondering: Why deliver updates two places?

---

### Post by vasa1 on 2016-06-24
I don't use Synaptic Package Manager a lot but I think its messages maybe more verbose.

There's also the bit about throttled releases. If you use the software center (and do a lot of reading as well) you may find that you don't immediately get certain updates: [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

But if you really, really want updates immediately, the commandline approach will oblige:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Updates via the commandline aren't subject to phased updates. So there's a chance, however small, that you may suffer!

---

### Post by UtnubuLap on 2016-06-24
So, if I understand you correctly, these 3 updates in "Ubuntu Software" have not been phased into "Software Updater" yet, but will be, once they have been confirmed safe?

In other words, running only "Software Updater" is sufficient to be up-to-date.

---

### Post by grahammechanical on 2016-06-24
> Why deliver updates two places?

Why have an application with a graphical user interface (GUI) to do updates at all? We can just use the command line. I would not want to use Linux if everything was done on the command line.

 Whatever GUI updater application we use it will only run the various commands. Install updates from the Details page and it will run Software Updater. On the other hand, Ubuntu Software interacts directly with the command line and that is because Ubuntu software is actually Gnome Software and the Gnome.org developers have their own ideas on how to do things.

This is life when we use a Free and Open Source Software (FOSS) distribution.

---

### Post by vasa1 on 2016-06-24
> **UtnubuLap said:**
> So, if I understand you correctly, these 3 updates in "Ubuntu Software" have not been phased into "Software Updater" yet, but will be, once they have been confirmed safe?

In other words, running only "Software Updater" is sufficient to be up-to-date.
No idea. I hope I didn't imply anything like that!

I use the commandline exclusively.

I'm guessing the present confusion will be sorted out by the time the first point release of 16.04 is available in July/August.

---

### Post by poorguy on 2016-06-24
> **vasa1 said:**
> 
But if you really, really want updates immediately, the commandline approach will oblige:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Updates via the commandline aren't subject to phased updates. So there's a chance, however small, that you may suffer!

I update using these commands is there a difference in the commands above.

sudo apt update && sudo apt upgrade

---

### Post by Impavidus on 2016-06-24
> **UtnubuLap said:**
> So, if I understand you correctly, these 3 updates in "Ubuntu Software" have not been phased into "Software Updater" yet, but will be, once they have been confirmed safe?

In other words, running only "Software Updater" is sufficient to be up-to-date.Yes to the second and more or less yes to the first. It's not really about confirming the update's safe. The updates are slowly distributed to all Ubuntu users in random order and the process is stopped if problems are detected. The packages have already been tested by those who like testing, but sometimes those tests fail to reveal a problem.

> **poorguy said:**
> I update using these commands is there a difference in the commands above.

sudo apt update && sudo apt upgrade

There's a tiny difference. The **apt upgrade** command may install new packages to satisfy dependencies when upgrading other packages, but will never remove a package. The **apt-get dist-upgrade** may both install new packages and remove packages to satisfy dependencies when upgrading other packages. But that rarely happens. In ten years of using Ubuntu, I've never seen a package being removed to upgrade another package.

---

### Post by pauljw on 2016-06-25
if you're going to use apt vs apt-get, i think apt full-upgrade is the equivalent to apt-get dist-upgrade.

---

