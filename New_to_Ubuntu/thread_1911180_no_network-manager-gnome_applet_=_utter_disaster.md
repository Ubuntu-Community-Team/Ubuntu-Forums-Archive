---
title: "no network-manager-gnome applet = utter disaster"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by jatwood on 2012-01-18
I'm looking for someone to help find a 15-minute fix for a problem I have inflicted upon myself. For reasons I'd rather not go into, I have inadvertently uninstalled "network-manager-gnome". I still however, have "network-manager" installed on my machine. I verified this by looking in synaptic package manager. I can't seem to connect to my home wifi because of this.

I say 15-minute fix as a bit of sarcasm because I have searched on this forum and online, and none of the solutions that I have seen provide a simple answer, but instead involve setting up a router, AP, and key (if desired) via bash. Many of the solutions also require creating and editing several configuration files. This is not something I want to do. If I have to go through and spend several hours configuring everything via CLI then I would assume just reinstall ubuntu altogether. Because it would take just as long. No offense to CLI, I just have better things to do.

I already have my Router, AP, essid, and WPA2 passphrase setup. I simply lost network-manager-gnome. Furthermore, I still have network-manager installed. I just don't have that applet that I'm so accustomed to on the panel anymore. I am familiar with bash and terminal, but as I mentioned above, if it takes an hour to just to get connected via CLI then I'd rather not even try.

I would appreciate the help from anyone who knows, or is willing to provide an answer to what appears to be a simple problem. I just can't seem to figure it out on my own. Thanks.

---

### Post by cariboo on 2012-01-18
Why not just connect to the router with a network cable, and re-install network-manager-gnome? With the network cable connected, open a terminal and type:

```
sudo dhclient eth0
```

assuming that your ethernet connection is eth0.

---

### Post by grahammechanical on 2012-01-18
You could try setting a liveCD as a software source and installing network-manager-gnome from the liveCD. It must be there as a package for installation.

Regards.

---

### Post by jatwood on 2012-01-18
"Why not just connect to the router with a network cable, and re-install  network-manager-gnome? With the network cable connected, open a terminal  and type: "

```
sudo dhclient eth0
```cariboo907, this solution worked. Also, the time required to do it < 30 seconds. I knew there was a simple fix out there. Thank you!!

Now for my next question: Why did the wired connection work, and not under a wireless connection?

I did try the following before I posted in these forums, with no success.

```
sudo iwconfig wlan0 essid <myessidhere>
sudo iwconfig wlan0 key <mykeyhere>
sudo dhclient wlan0
```Just curious for the sake of gaining more insight.
I appreciate you guys helping me get this fixed. I realize that I have a lot more to learn about networking.

---

