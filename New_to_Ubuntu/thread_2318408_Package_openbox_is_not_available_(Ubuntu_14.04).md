---
title: "Package openbox is not available (Ubuntu 14.04)"
date: 2016-03-25
forum: New to Ubuntu
---

### Post by ryan210 on 2016-03-25
Hi everybody! I'm trying to download x11 for some school assignments because apparently I don't already have it (running Ubuntu 14.04), but when I try "  sudo-aptget install xorg openbox ", I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openbox' has no installation candidate


Any ideas on how to fix this? I also tried " sudo apt-get update ", but I get another error:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


Really appreciate any feedback. Thanks!

---

### Post by deadflowr on 2016-03-26
If you're on Ubuntu desktop, you're on X11.
servers are, of course, a different story.

As far as the google error.
You need to add a small section to the google sources.list entry
Follow this post to fix that:
[http://ubuntuforums.org/showthread.php?t=2315941&p=13449789#post13449789](http://ubuntuforums.org/showthread.php?t=2315941&p=13449789#post13449789)

then re-try the apt-get update command, 
you will also want to run the* apt-get upgrade* command to install the updates found in the apt-get update command.
You want to run the upgrade command, so the system will be up-to-date, and the likelihood of errors when you try to install anything, will be less.
(Hint: the upgrade command can seem misguided, but do not worry, it is the actual command to install the normal updates. The update command only determines if the system can get new updates or not. It can be confusing, and some users think that the upgrade command will upgrade Ubuntu to a newer version that they did not want. So relax, it will not do that.)

If any problems, post the output for the apt-get update command.


**Edit:** I noticed you marked this thread as solved.
It does not seem to be the case, so I've removed the solved prefix.

Having the solved prefix, would deter others from helping, since it would be assumed that you fixed the problem so no other assistance would be needed.

---

### Post by grahammechanical on 2016-03-26
Openbox is

> Openbox is a highly configurable, next generation window manager with extensive standards support.

x11 openbox is not in the Ubuntu repositories but I think that openbox is in the repositories. So, if it is openbox that you need to install then search Ubuntu Software Centre for openbox.

Once installed you can log in to an Openbox session at the Ubuntu login screen. Click the Ubuntu icon at the top right of the password panel and there should be a drop down menu that will let you select Openbox as the window manager for that session.

The openbox web site speaks of Gnome/Openbox. For your information, Ubuntu is built on the Gnome 3 desktop environment. So, you do not need to install Gnome.

[http://openbox.org/wiki/Main_Page](http://openbox.org/wiki/Main_Page)

Regards.

---

### Post by vasa1 on 2016-03-26
> **ryan210 said:**
> Hi everybody! I'm trying to download x11 for some school assignments because apparently I don't already have it (running Ubuntu 14.04), but when I try "  sudo-aptget install xorg openbox ", I get this:
...
Can you go into any detail about these assignments? What exactly do you need to do?

I don't know how much you know or don't know, but running an Openbox session isn't a very user-friendly experience unless you're willing to spend time figuring it out.

---

### Post by buzzingrobot on 2016-03-26
Openbox is, indeed, in the repository.  Several other packages will be needed to configure Openbox as a practical window manager.

It looks like the OP has installed Chrome, and that the repo file it behind is faulty in some fashion, or perhaps the server was offline for a bit.  

In any case, the OP might try disabling the Chrome repo:  Launch the Update Manager, enter the settings sections, de-click the Google Chome repo, then close the app.  Before it closes, it will do a refresh.  If other errors show at that time, then something else is wrong. Otherwise, open a terminal and install openbox.

If the OP is using any desktop version of Ubuntu, xorg is already there.  It's a core component.

---

### Post by vasa1 on 2016-03-26
> **buzzingrobot said:**
> ...  Several other packages will be needed to configure Openbox as a practical window manager.
...
Not really. A panel, tint2 or lxpanel, is enough.

---

### Post by oldos2er on 2016-03-27
I'm on 15.10, but I see openbox is in the universe repository. Do you have that enabled? If this is a new install, have you run ```
sudo apt-get update
``` ?

---

### Post by vasa1 on 2016-03-27
> **oldos2er said:**
> I'm on 15.10, **but I see openbox is in the universe repository**. Do you have that enabled? If this is a new install, have you run ```
sudo apt-get update
``` ?
I never thought of that. I took it for granted because it's installed by default with Lubuntu.

---

### Post by oldos2er on 2016-03-27
Yeah, I don't think it's installed by default on any other flavor. I run Xubuntu, FWIW.

---

### Post by vasa1 on 2016-03-27
*xfwm4* is also in universe. I haven't checked in a while and so I'm wondering if universe is enabled by default in *buntu flavors.

I'll check that the next time I boot up a 16.04 Live USB.

---

### Post by buzzingrobot on 2016-03-27
> **vasa1 said:**
> Not really. A panel, tint2 or lxpanel, is enough.

Three is "several", right? ;)

---

### Post by deadflowr on 2016-03-27
All flavors, except normal Ubuntu need universe to be enabled during install.
Since they all depend on the packages in there.
(Ubuntu can live without it, since all Ubuntu's default packages are in the main repo)

--I think one exception was Kubuntu 12.04, when that was still a Canonical product.


anyhoo, let's wait for a reply some day, from the OP.

---

### Post by vasa1 on 2016-03-27
> **buzzingrobot said:**
> Three is "several", right? ;)
Let me rephrase "A panel, tint2 or lxpanel, is enough." to *a panel such as tint2 _or_ a panel such as lxpanel _is_ enough* ;)

---

### Post by vasa1 on 2016-04-03
> **vasa1 said:**
> *xfwm4* is also in universe. I haven't checked in a while and so I'm wondering if universe is enabled by default in *buntu flavors.

I'll check that the next time I boot up a 16.04 Live USB.

This is what /etc/apt/sources.list has on the Lubuntu 16.04 (beta) live USB:```
deb cdrom:[Lubuntu 16.04 LTS _Xenial Xerus_ - Beta amd64 (20160402)]/ xenial main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse

```
And then:
```
lubuntu@lubuntu:~$ sudo apt install -s xfwm4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfce4 xfwm4-themes
The following NEW packages will be installed:
  xfwm4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Inst xfwm4 (4.12.3-1ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf xfwm4 (4.12.3-1ubuntu2 Ubuntu:16.04/xenial [amd64])

```Anyway, OP seems to have ... :confused:

---

