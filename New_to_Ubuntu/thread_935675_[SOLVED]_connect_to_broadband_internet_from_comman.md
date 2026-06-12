---
title: "[SOLVED] connect to broadband internet from command line"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by radiantarchon on 2008-10-01
i acccidentally uninstalled both kde and gnome and are now in a dos like interface. i coud fix most of the problems i'm having myself. but it wont let me connect to the internt net so
sudo apt-get -f install does not work. i was wondering how to accoplish this from the command line

---

### Post by tubasoldier on 2008-10-01
oh the drawbacks of networkmanager.
completely useless in the command line. 

You will have to setup your internet connection manually. I havent done it in quite a while so I am unable to give you the real rundown of how to do it.

You will need ifup/ifdown/ifconfig tools

---

### Post by radiantarchon on 2008-10-01
i have those tools and i also have ubuntu on a dvd. could i get the files  apt-get -f install is asking for from it?

---

### Post by iaculallad on 2008-10-01
> **radiantarchon said:**
> i have those tools and i also have ubuntu on a dvd. could i get the files  apt-get -f install is asking for from it?

You could if those files are pre-packed within the Ubuntu DVD media. Try:

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get -f install
```

---

### Post by radiantarchon on 2008-10-01
the dvd thing did not work. i guess i have to manually configure the internet. anybody know how?

---

### Post by lswb on 2008-10-01
For a wired ethernet connection try this at the command line:
```

sudo ifconfig eth0 up
sudo dhclient eth0

```
eth0 is the default ethernet interface name, if your system uses a different ethernet port to connect, substitute that name for eth0.

If you connect via wifi it is a little trickier. Assuming a wireless interface name of eth1, and an unsecured network (no WEP or WPA) with the name "mynetwork"
```

sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed essid "mynetwork"
sudo ifconfig eth1 up
sudo dhclient eth1

```

If your network uses WEP or WPA you need to know the pass key in hex, and make the 2nd line:

sudo iwconfig eth1 mode managed essid "mynetwork" key KEYINHEXDIGITS


Also, you indicated you have the live cd, if so you can edit /etc/apt/sources.list to add it. The file must be edited as root. Make a backup of the file first

cd /etc/apt
sudo cp sources.list sources.list.back
sudo vi sources.list

Or use nano or whatever editor you have available instead of vi. The line to add is:
```

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

```

To reinstall gnome:

apt-get install ubuntu-desktop

---

### Post by lswb on 2008-10-02
sorry, double posted

---

