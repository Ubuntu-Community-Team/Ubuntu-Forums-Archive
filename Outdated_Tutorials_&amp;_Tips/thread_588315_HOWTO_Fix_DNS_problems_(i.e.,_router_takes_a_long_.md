---
title: "HOWTO: Fix DNS problems (i.e., router takes a long time to load all web sites)"
date: 2007-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by bmartin on 2007-10-23
[COLOR="Red"]When following this guide, know that there is no support, and the guide is to be used at your own risk.[/COLOR] Sorry, but I have a lot of other threads to support. I will help you to the best of my ability, but I can't guarantee success or that your system will continue to be functional. Don't try to fix something that isn't broken; [COLOR="Red"]if your DNS works fine already, you're probably best leaving it as it is.[/COLOR]

Thanks go to the everyone at opendns.com who made the OpenDNS system possible.

These steps were tested on Ubuntu Feisty Fawn (7.04) and Gutsy Gibbon (7.10).

If you're having trouble with your wireless connection taking a long time to look up web sites, it might be your DNS settings that are to blame. I was having a hard time on several different computers. I tested my ping speed to the router, which was fine. I tried several different operating systems. I updated my router's firmware, changed the wireless channel, and tried different security modes, but nothing worked. I called Belkin's tech support; that was a waste of time.

I have a Belkin F5D7230 router. I tried updating the DNS servers on that, but it was to no avail.

The only way to get everything working was to manually modify what servers my computer used to look up web sites. This guide will do the same for you. Other than lightning-fast DNS resolution, there are other tangible benefits. To see what OpenDNS can do for you, visit them at [opendns.com]("http://opendns.com/")

[LIST=1][*]Before modifying anything, **always** back up whatever you're going to modify. We'll back up the file we're going to modify right now. Open up a terminal and back up your resolv.conf file:
```
sudo cp /etc/resolv.conf /etc/resolv.conf.bak
```
[*]Edit the /etc/resolv.conf file so that your router's IP address is commented out:
```
sudo gedit /etc/resolv.conf
```
The text file should look similar to this (except for the search line):
```
search Belkin
#nameserver 192.168.2.1
```
[*]OpenDNS has some good instructions on setting up their DNS service [here]("https://www.opendns.com/start?device=ubuntu"). Alternatively, you can manually add the DNS IP addresses listed there, if you like using the terminal.[/LIST]
To undo these changes, use the following command:
```
sudo cp /etc/resolv.conf.bak /etc/resolv.conf
```

---

