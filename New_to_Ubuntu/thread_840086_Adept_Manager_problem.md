---
title: "Adept Manager problem"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bobmac on 2008-06-25
Folks,

I've tried to install the KDE package from the Administration|Synaptic Package Manager. When I did a search for KDE the system displayed something called the Adept Manager which seemed to be something to do with the KDE package so I selected to install it.
When I rebooted as requested after the install I located it under Applications|System Tools. However when I tried to start the Adept Manager I got the following message:

You will not be able to change your system settings in any way (install, remove or upgrade software), because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions.

I'm now not sure if I've installed the correct stuff and even if I have I have no idea on what commands I can use to get KDE up and running.

Any help will be gratefully appreciated.

Bob

---

### Post by Kevbert on 2008-06-25
Adept Manager is the equivalent KDE application to Add/Remove and the Synaptic Package Manager.  You can update/install programs as usual with the terminal.

---

### Post by bobmac on 2008-06-25
Kevbert,

Many thanks for your quick reply to my query. However, your answer has me even more confused than I was. Does this mean that I've installed the wrong thing? What I really wanted to do was install the KDE environment.

Bob

---

### Post by Kevbert on 2008-06-25
Basically you can use terminal for updating as normal (using sudo, for admin) when you run either gnome or KDE environments.  When running Gnome you can update via Synaptic (I don't know if you'll see the Adept Manager, as I run KDE - Kubuntu as a separate OS).  When in Gnome the preferred update manager is Adept which you can get to via System - Adept Manager (again I don't know if you can see this in Gnome but you probably can via System-Admin).  
Adept Manager is quite a nice graphical interface.  First you have to download the updates and then you need to select apply.
It's very possible that Adept isn't required but it's probably best to leave  it on your system as both Adept and Synaptic may use shared resources (drivers, programs) and uninstalling may cause additional problems.
It looks like you haven't installed the KDE interface.  Please have a look at [[COLOR="Red"]this[/COLOR]]("http://www.howtogeek.com/howto/ubuntu/install-kde-kubuntu-on-ubuntu/").

---

### Post by meindian523 on 2008-06-25
You can install the kde environment by ```
sudo apt-get install kubuntu-desktop
```

---

### Post by angry_johnnie on 2008-06-25
Adept is, pretty much, Kubuntu's version of Synaptic, and you don't really need it.

It tells you that you won't be able to install or change anything because, like synaptic, it has to be opened with root permissions. (gksu, for gnome; kdesu, for KDE)

If you only want the KDE environment, you could install it by entering this in a terminal:

```
sudo apt-get install kde-core
```

It will be a very basic KDE setup, but it works fine.  If you install the entire kubuntu-desktop metapackage, it will add a whole lot of stuff you may not really need or want.

As a side note:  if you use apt-get to install it, it would be a good idea to write down all the packages that are going to be installed (it will warn you: the following packages are going to be installed...).  That way, if you ever feel like removing it, you'll know exactly what to remove.

---

