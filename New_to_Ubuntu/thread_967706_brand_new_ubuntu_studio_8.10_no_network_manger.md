---
title: "brand new ubuntu studio 8.10 no network manger?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Arthur Millar on 2008-11-02
i have just installed the new Ubuntu-studio ibex 
my lan card has had no support for 8.04 or 8.10 or studio8.l0
i know how to install the driver I need on hardy and ibex 
but the 8.10studio version has no network manager(no icon in the top corner or on my system menu's) 
the proprietary driver I'm using is active but still nothing i know it worked in ibex 8.10 so why not in studio8.10 ?

during the install i had to skip the network auto detection because i had to setup the driver first

---

### Post by PriceChild on 2008-11-02
You can check if the network manager is installed with:```
apt-cache policy network-manager-gnome
```Then try```
nm-applet
``` to see if that launches the applet near the clock.

---

### Post by Arthur Millar on 2008-11-02
the package is definitely missing 
its not on the install disk either?
w: unable to locate package network-manager-gnome

---

### Post by Arthur Millar on 2008-11-02
eish ok so i guess i need to install the package manually
and all its dependents as well 
thats gonna take a while :)

---

### Post by rhenium3 on 2008-11-02
how do I install the package??? :(

---

### Post by Arthur Millar on 2008-11-02
i am back online 

i needed a few packages which i downloaded from here
[http://packages.ubuntu.com/intrepid/net/network-manager-gnome](http://packages.ubuntu.com/intrepid/net/network-manager-gnome) 

i downloaded all the dependents to be sure although you only need these 

1.libnm-util0
2.libnm-glib0
3. network-manager 
4. network-manager-gnome 

install them in that order and it should work after reboot

---

### Post by rhenium3 on 2008-11-02
How? I did sudo apt-get install network-manager-gnome and I got this:

[B]rhenium3@rhenium3-laptop:~$ sudo apt-get install network-manager-gnome
[sudo] password for rhenium3: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  network-manager-gnome: Depends: network-manager (>= 0.7~~svn20080928) but it is not going to be installed
E: Broken packages
[/B]

---

### Post by Arthur Millar on 2008-11-02
> **rhenium3 said:**
> How? I did sudo apt-get install network-manager-gnome and I got this:

The following packages have unmet dependencies:
  network-manager-gnome: Depends: network-manager (>= 0.7~~svn20080928) but it is not going to be installed
E: Broken packages
[/B]

this need to be installed in the order from my previous post

1.libnm-util0
2.libnm-glib0
3. network-manager
4. network-manager-gnome

install them in that order and it should work after reboot

---

### Post by Arthur Millar on 2008-11-02
> **rhenium3 said:**
> How? I did sudo apt-get install network-manager-gnome and I got this:

The following packages have unmet dependencies:
  network-manager-gnome: Depends: network-manager (>= 0.7~~svn20080928) but it is not going to be installed
E: Broken packages
[/B]

the dependent files need to be installed in the order of my previous post

1.libnm-util0
2.libnm-glib0
3. network-manager
4. network-manager-gnome

install them in that order and it should work after reboot

---

### Post by deadly_sinn on 2008-11-03
i think what is missing is that you have to manually dowload the packages, meaning go to the website on another pc...
anywhoo, i still have a problem..im using a wireless modem and i cant set it up at all..cant even see it..it is detected but no access to it, and i cant change things in network manager either..im super confused..any clues?

---

### Post by Arthur Millar on 2008-11-03
> **Arthur Millar said:**
> eish ok so i guess i need to install the package manually
and all its dependents as well 
thats gonna take a while :)

yep

---

### Post by shreaded_teddy on 2008-12-19
i just did what you guys said and installed the gnome network thing but i'm still not getting anything.  in the network manager thing in the start menu it only shows network loopback for lan and no wlan card but no internet connection.  i've got an e1505 dell laptop if that helps.  would it be easier to install the regular ubuntu then apt-get the ubuntu studio stuff?

---

### Post by TehBleachBottle on 2009-04-10
I also am having the same problem concerning the network manager. I have a Dell Studio 1537 laptop and only see my ethernet and loop feedback in my network tools. Do I need to install the packages? If so, is it possible that a package containing *all* of the network manager files is available somewhere? It would make life a tad easier. Much thanks.

---

### Post by regaladys on 2010-11-20
is this still applicable for 10.10?

---

