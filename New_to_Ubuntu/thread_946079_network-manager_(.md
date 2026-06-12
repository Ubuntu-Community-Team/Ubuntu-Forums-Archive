---
title: "network-manager :("
date: 2008-10-13
forum: New to Ubuntu
---

### Post by VoodooLoveDog on 2008-10-13
Ok. So I was trying to get vpnc installed an working to connect to an ASA firewall. I was having problems so I ran the command:

sudo apt-get remove vpnc

However, when I did that, it left the vpn connections menu item in network-manager. I then decided to give the Cisco created vpn client (4.8) a go. But I was having problems with that one. So I decided to reinstall vpnc, but when I did, the menu tab complained that "no suitable software..." so I couldn't create a vpn profile.

I figured the best way to deal with this (much to discredit) is to remove network-manager and have ubuntu reinstall it. But now, I can't find it in the synaptic package manager anymore and when I choose it in add/remove it gives me an error about not being an i386 package. If I run:

sudo apt-get install network-manager from the CLI, it tells me that there is no candidate in the sources.list. 

So can anyone give me an idea as to how to get network-manager back on my PC?

---

### Post by Pelham123 on 2008-10-13
Are you running 32-bit or 64-bit ubuntu?

#######################################

> **VoodooLoveDog said:**
> If I run: sudo apt-get install network-manager from the CLI, it tells me that there is no candidate in the sources.list.

This may point to a repository error. To rule this out though can you post your /etc/apt/sources.list?

#######################################

> **VoodooLoveDog said:**
> Can give me an idea as to how to get network-manager back on my PC?

Removing network-manager also removes network-manager-(gnome/kde). Have you tried installing network-manger-gnome ?

---

### Post by hyper_ch on 2008-10-13
don't know what the default network manager in ubuntu is called but you might want to have at another nm. I presonally prefer now using WICD --> [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by VoodooLoveDog on 2008-10-13
> **Pelham123 said:**
> Are you running 32-bit or 64-bit ubuntu?

#######################################



This may point to a repository error. To rule this out though can you post your /etc/apt/sources.list?

#######################################



Removing network-manager also removes network-manager-(gnome/kde). Have you tried installing network-manger-gnome ?

I do not have the option to install network-manager-gnome either. Here is the uncommented portion of my sources.list:

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

#
#

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse


deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted


Thanks for your help.

---

### Post by Pelham123 on 2008-10-13
OK.

Chuck in your Ubuntu Cdrom and try these commands:
```

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install network-manager
```

See what the reply is...

---

