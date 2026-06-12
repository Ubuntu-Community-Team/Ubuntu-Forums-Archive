---
title: "Wireless networking slow to start"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by ThreeTrees on 2008-05-16
Hi, I'm relatively new to Ubuntu; I installed Gutsy (7.10) on my Sony Vaio SZ780 a few months ago, and I upgraded to Hardy Heron (8.04) about a week and a half ago.  However, the problem I'm having with networking was also a problem with Gutsy, so it's not an upgrade issue (although I had hoped it would be fixed):

Wireless networking works, but it is usually slow to start.  That is, after I boot up Ubuntu and log in, most of the time the networking applet thingie on the top right (nm-applet 0.6.6) says I don't have networking.  After some time, which could be up to 15 minutes or more, I see the applet icon spinning, and then I get networking.  What's weird is even when I don't have networking, it will often show me *other* wireless networks in the neighborhood!  Sometimes four or five of them -- every one but mine!  Less often, I will be able to see and use my own network right away after I boot up, but it seems random.

I would appreciate any ideas.  Thanks!

*As extra incentive to solve this problem, I note that I have dual boot, and Windows XP doesn't have this problem.  :)  Don't worry --  I'm not abandoning Ubuntu, but it's sometimes frustrating to have to wait when I want to get online right away.*

---

### Post by jbrown96 on 2008-05-18
What type of wireless card do you have? You can find it in the ouput of```
lspci
```

There may be something specific to your card that you can find out. NetworkManager may also be a problem. There is a pre-release version of NetworkManager 0.7.0 available that is a lot faster, although I'm not sure it will solve your entire problem. The only problem is that the connection editor does not work.
Add these lines to your /etc/apt/sources.list
deb [http://ppa.launchpad.net/asac/ubuntu](http://ppa.launchpad.net/asac/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/asac/ubuntu](http://ppa.launchpad.net/asac/ubuntu) hardy main
Refresh the package list. Then, in synaptic, search for networkmanager and install the 0.70 version of both network-manager and gnome-network-manager

---

### Post by ThreeTrees on 2008-05-20
Here's the relevant line from lspci:

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

Thanks for helping!

---

### Post by gnomikos on 2008-05-20
```
iwlist eth1 scanning
```

lists available networks(replace eth1 with your interface)

Try it when network manager cannot find your network.

If it is a problem of network manager, i suggest installing wicd.

---

