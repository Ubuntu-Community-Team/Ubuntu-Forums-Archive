---
title: "I am new to linux, xubuntu core, help install browser"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by zancudo2 on 2016-03-06
I am new using linux, I downloaded Xubuntu core, but it does not even have a text editor, or archive manager!  Could someone help me install Firefox browser, a text editor and archive manager?

---

### Post by Bucky Ball on 2016-03-06
Welcome. Open a terminal and:

> sudo apt-get install synaptic

Once that is done, look in the menu for Synaptic Package Manager. You can search and install what you want from there. You can install whatever you want via the terminal, but Synaptics is a little more friendly for newcomers. :)

---

### Post by v3.xx on 2016-03-06
Also have a look at the package of anything you load up and see what your getting.

[http://packages.ubuntu.com/wily/xubuntu-core](http://packages.ubuntu.com/wily/xubuntu-core)

And you do have a text editor, its called nano.

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

PS
SPM contains all package info.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by Bucky Ball on 2016-03-06
> **v3.xx said:**
> 
And you do have a text editor, its called nano.

Think OP may be looking for a GUI text editor as in Abiword, Leafpad, or Libreoffice rather than a terminal text editor, none of which are installed in x-core (though there are a couple of terminals). ;)

Xubuntu-core is very lean.

---

### Post by oldos2er on 2016-03-06
> **zancudo2 said:**
> I am new using linux, I downloaded Xubuntu core, but it does not even have a text editor, or archive manager!  Could someone help me install Firefox browser, a text editor and archive manager?

If you want Xubuntu's default programs, install xubuntu-desktop.

---

### Post by tom-bellas3rd on 2016-03-06
I would recommend installing something more complete for a new user to the linux world. It might be easier to just download the xubuntu normal iso, or if your computer can handle it, the Ubuntu desktop, which has a more fleshed out desktop experience. 

Installing the slimmed down core version might not be ideal for a new user as you are not familiar with whats out there in terms of apps for Linux.

just my two cents.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Bucky Ball on 2016-03-06
> **tom-bellas3rd said:**
> It might be easier to just download the xubuntu normal iso, or if your computer can handle it, the Ubuntu desktop, which has a more fleshed out desktop experience. 

No need. As oldoser2 posted, just install xubuntu-desktop if you want a standard Xubuntu. Achieves the same as installing it pretty much. 

@OP: Installing xubuntu-desktop will leave you with Xubuntu, but that advice assumes you haven't installed xubuntu-core for a specific reason. If you have, installing xubuntu-desktop defeats the purpose of installing xubuntu-core. ;)

---

### Post by buzzingrobot on 2016-03-06
> **zancudo2 said:**
> I am new using linux, I downloaded Xubuntu core, but it does not even have a text editor, or archive manager!  Could someone help me install Firefox browser, a text editor and archive manager?

xubuntu-core is not the usual way to install Xubuntu.  It's a minimal setup that deliberately contains few software packages.

Be aware that while it is common in Windows to download an archive of software from an independent site and then extract it and run an installer contained within that archive, this is done very rarely in Linux. Distributions, like Ubuntu, maintain software on servers (repositories) and include a tool (package manager) to download and install software packages.  

The package manager keeps track of what's been installed on your system and also handles the updates.  We generally do not deal directly with the package manager, but use easier and more useful front-end programs.  Some, like Synaptic, are GUI's,  Others, like apt-get, are command line tools. 

There's a lot more here: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by zancudo2 on 2016-03-06
not working, the message is "package not found, but it is referred to another package, package missing, obsolete or available from another source"

---

### Post by oldos2er on 2016-03-06
Which version are you using? Have you tried ```
sudo apt-get update
``` ?

---

### Post by zancudo2 on 2016-03-06
Xubuntu core 15.10,              Yes, I tired, but nothing happens,  " not available, but it is referred to another package, means it is obsolete, missing or only available from another source"     is it possible to install at least a browser using the terminal?

---

### Post by vasa1 on 2016-03-06
Could you explain why you went the xubuntu core route if you're "new to linux"? Maybe the Xubuntu team would add a caveat to their documentation about the target audience for xubuntu core.

---

### Post by matt_symes on 2016-03-07
Hi

> **tom-bellas3rd said:**
> I would recommend installing something more complete for a new user to the linux world. It might be easier to just download the xubuntu normal iso, or if your computer can handle it, the Ubuntu desktop, which has a more fleshed out desktop experience. 

Installing the slimmed down core version might not be ideal for a new user as you are not familiar with whats out there in terms of apps for Linux.

just my two cents.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

> **vasa1 said:**
> Could you explain why you went the xubuntu core route if you're "new to linux"?

Agreed.

Kind regards

---

### Post by oldos2er on 2016-03-07
> **zancudo2 said:**
> not working, the message is "package not found, but it is referred to another package, package missing, obsolete or available from another source"

Please post output of both commands: ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
```

---

### Post by slickymaster on 2016-03-07
> **vasa1 said:**
> Could you explain why you went the xubuntu core route if you're "new to linux"? Maybe the Xubuntu team would add a caveat to their documentation about the target audience for xubuntu core.

Xubuntu Core was introduced in May, 2015 and by the time it was introduced it was clearly stated that it's a slimmed down version of Xubuntu, not coming with all the additional features of a full and modern desktop. Essentially it only ships Xfce and the basic look and feel of Xubuntu, so there will be no office suite, media players, et cetera. See [http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/)

As for adding a caveat to the shipped documentation it was't dimmed as necessary since it didn't fall under its scope, which is to provide information on some of the most common issues with Xubuntu.
But as everything this isn't a written in stone rule, so whomever feels otherwise, please file a bug on the source package in Ubuntu at [http://bugs.launchpad.net/ubuntu/+source/xubuntu-docs](http://bugs.launchpad.net/ubuntu/+source/xubuntu-docs).

---

### Post by grahammechanical on 2016-03-07
I have just installed Xubuntu core so that we can clear up a few things.

1) According to the Xubuntu core documentation we are told to download the mini ISO image. This is not a Xubuntu core mini ISO image but a Ubuntu mini ISO image. But we can get to a Xubuntu minimum installation from it. And all it is a Xubuntu command line.

2) Run the mini ISO Cd and we get an Installer boot menu with these four options

a) Install
b) Command-line Install
c) Advanced options
d) Help

I chose Install and after providing the usual user information similar to using the Something Else option the Ubuntu base system installed.

3) At some point in the process we are asked to choose which software to install. At the top of the list is Basic Ubuntu Server but all the desktop environments are in the list including Xubuntu Desktop & Xubuntu Minimum Installation.

4) I choose Xubuntu Minimum Installation and what I got was a Xubuntu command line. Well, I didn't expect anything else.

5) Following the Xubuntu core documentation I then installed xubuntu-core

```
sudo apt-get install xubuntu-core
```

That brought in lots and lots of stuff including Xfce4.  A restart (sudo shutdown - r now) brought me to an Xfce4 desktop environment. That is more like it!

6) It does have a web browser. Debian Sensible Browser which not very sensibly failed to load. So, I opened the terminal and installed Firefox. And here I am posting from Firefox on Xubuntu core.

A question for Zancudo2

When the install process got to the point where it provided a dialog labeled Choose Software to Install, what option did you choose? If you choose Xubuntu Minimal Installation you now need to run

```
sudo apt-get install xubuntu-core
```

And take it from there.

Regards.

Edit: After a bit of research I have found out that sensible browser is not a web browser at all but a kind of command to launch the default installed web browser.  Sorry, Xfce4 devs.

---

### Post by Bucky Ball on 2016-03-07
@grahammechanical: Not sure why you went the long way unless you specifically wanted Xubuntu-core 14.04. The community ISOs for [Xubuntu-core are here]("https://unit193.net/xubuntu/core/") and are installed as per normal. They have been available since 14.10 or 15.04 from memory. No mini install required. ;)

---

### Post by slickymaster on 2016-03-08
> **Bucky Ball said:**
> @grahammechanical: Not sure why you went the long way unless you specifically wanted Xubuntu-core 14.04. The community ISOs for [Xubuntu-core are here]("https://unit193.net/xubuntu/core/") and are installed as per normal. They have been available since 14.10 or 15.04 from memory. No mini install required. ;)

Well, Unit193 just made that link public after 15.04 release. But you're right, no mini install required.

---

