---
title: "[SOLVED] trouble installing .deb file"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-01
i am trying to install the kppp.deb file via terminal because i do not have Internet connection on my Ubuntu amd64 pc, however i have used the command dpkg -i kppp.deb file but i get error messages and have to uninstall the package.



following message in terminal is shown when attempting to install deb package.

"dpkg dependency problems prevent configuration of kppp

kppp depends on kdelibs4c2a, however kdelibs4c2a is not installed

kppp depends on libqt3-mt, however libqt3-mt is not installed"

does any one know what this means

---

### Post by drs305 on 2008-10-01
It means that those 2 packages, kdelibs4c2a and libqt3-mt, are not installed but are required by the package you are trying to install. Both of these are listed in synaptic. 

*If you can get an internet connection:*
Try installing these and then installing the deb again. It may install or it may show you more dependent packages. 

Use synaptic or to install these two via the command line (close synaptic before running this command):
```
sudo apt-get install kdelibs4c2a libqt3-mt
```

If they are on the livecd and you have the cdrom enabled in synaptic, you could install them from synaptic. If you find them on another cd you can enable the cd via the Repositories, Third Party, Add option.

Added: You can also highlight the package in synaptic (if available) and hit "Properties" then "Dependencies" to see what packages are required or recommended for the installation.

---

### Post by kansasnoob on 2008-10-01
> **fr.theo said:**
> i am trying to install the kppp.deb file via terminal because i do not have Internet connection on my Ubuntu amd64 pc, however i have used the command dpkg -i kppp.deb file but i get error messages and have to uninstall the package.



following message in terminal is shown when attempting to install deb package.

"dpkg dependency problems prevent configuration of kppp

kppp depends on kdelibs4c2a, however kdelibs4c2a is not installed

kppp depends on libqt3-mt, however libqt3-mt is not installed"

does any one know what this means

kppp is already in the repos so you can install it either from synaptic or command line.

I'd suggest using synaptic since there is a possibility of the package requiring adding or removing various other packages. What I do is bust out the old spiral notebook and actually write down the names of all packages being added or removed. It makes life much easier if you end up with a broken system after making changes.

NOTE: There is also a kppp-kde4 package so double check what version of KDE is installed. Just use the search feature in synaptic - type in kde and see which version you're running (I think), I don't have a Kubuntu box here at the moment.

---

### Post by fr.theo on 2008-10-01
my major problem is that i have no internet connection on that pc so it is hard to acquire any applications or dependencies so i am in a bit of a pickle.

---

### Post by drs305 on 2008-10-01
> **fr.theo said:**
> my major problem is that i have no internet connection on that pc so it is hard to acquire any applications or dependencies so i am in a bit of a pickle.

I checked and, unfortunately, as suspected, neither is on the install cd.

---

### Post by kansasnoob on 2008-10-01
Is this Ubuntu or Kubuntu?

I notice it's "flagged" as Ubuntu. If so ppp support should be installed (I think), I've only done a couple of these dial-up jobs and they've been over 6 months ago.

Is this helpful at all:

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by _duncan_ on 2008-10-03
How about using gnome-ppp instead? It's less than 1 MB in size, and all the dependencies are already available in a default ubuntu gnome install. So it's more practical to download elsewhere and install with dpkg -i gnome-ppp.

Last time I installed kppp on a default ubuntu gnome desktop, it required 30 MB download (7 or 8 packages including dependencies) using Synaptic package manager. Very time consuming to hunt down all the dependent packages if not done thru a package manager.

Another option is to get one of the built-in command-line dialers (wvdial or pppconfig) working so you have at least internet connection in your ubuntu box, then use a package manager to install kppp within ubuntu if you want a graphical dialer.

---

