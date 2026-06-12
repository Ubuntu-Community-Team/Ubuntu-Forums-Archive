---
title: "HOWTO: Install Xubuntu on machine 128mb RAM with graphical configs for Network etc."
date: 2006-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by chanders on 2006-06-26
Recently one of my friends wanted to reinstall windoze xpee on his Dell Inspiron 4100 (128MB Ram), so I suggested he use Linux and he agreed to let me install it alongside xpee.

Little did I know that the Ubuntu installer would bork on 128MB ram when I tried to do the install. So I downloaded the Xubuntu installer. This also borked, taking up to 45mins to move from one step to the other, eventually crashing the installer on step 3.... ](*,) 

This is quite sad/embarassing seeing that xpee installed perfectly and was up and running in no time... :evil: 

I finally got it working following these steps...

Step 1: Download the ISO for the ALTERNATE CD [URL="http://mirror.cs.umn.edu/ubuntu-releases/6.06```

```/ubuntu-6.06-alternate-i386.iso"]here[/URL] and burn it on a CD

Step 2: Reboot the machine with the CD and then it shows the prompt "boot: " type **server** and press enter. This will take you through a typical install etc. However it does not setup the network. When it reboots, you will be at a command prompt. Login with your login credentials.

Step 3: You will now need to configure your network. Type
```
sudo pico /etc/network/interfaces
```

make sure the eth0 (eth1 etc.) section looks like this for DHCP

```
auto eth0
iface eth0 inet dhcp
```

or like this (substitute your settings) for a STATIC IP address

```
auto eth0
iface eth0 inet static
address 10.1.148.129
netmask 255.255.255.0
gateway 10.1.148.1
```

then press ctrl+o and press enter to save
then press ctrl+x to exit

Step 4: Set up your DNS
```
sudo pico /etc/resolv.conf
```

Make sure you have the IP for your DNS look like this (substitute your own)
```
nameserver 12.152.107.199
```

again ctrl+o then ctrl+x

Step 5: Edit your sources.list file
```
sudo pico /etc/apt/sources.list
```

Remove all #'s that start a line from in front all the deb's 

eg. make

# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

look like 

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

etc, for all lines..... again ctrl+o then ctrl+x

Step 6: Type 

```
sudo apt-get update

```

Step 7: Restart your machine 

Step 8: Type 

```
sudo apt-get install xubuntu-desktop

```

answer y for the question... then wait for it to install....

Step 9: Type

```
sudo apt-get install gdm
```

Step 10: Type 

```
sudo apt-get install gnome-system-tools
```

It will say it's going to remove xubuntu-system-tools, dont worry... just say y

Step 11: Restart your machine... login and now you're in Xubuntu

Step 12: Should you need to change any network settings you can use the graphical way by clicking on "Networking" in the menu instead of the command line way like we did above....

Thats it! Questions, comments welcome...

---

### Post by jISh on 2006-07-09
That seems like a decent method, but one question:
If you install the server Ubuntu distro, it doesn't get the same updates as normal desktop distro, am I right? It's not exactly the same thing as a regular install...

Anybody want to confirm this? If it's false, then I'm definatley gonna go do this on my laptop...

---

### Post by BetaguyGZT on 2006-07-09
It gets all the updates like normal. ^_^

---

### Post by ohyeah on 2006-11-11
Thank you so much for this guide!  I was in the same situation and thought I was the only one.](*,)

---

### Post by venkatmangudi on 2006-11-26
:D 
I ran into the same problem installing Ubuntu on my really old Celeron desktop with 128 MB RAM. After spending a lot of time trying different options, I downloaded Xubuntu Edgy and the install is running like a well oiled machine as I type this message. 

On the Edgy, though the updated splash screen makes a nice addition to the ease of the install process. I was worried about it detecting the Netgear Wifi PCI card, but it was such a great feeling to know that it was auto detected. Couldn't be more happier to give Win 98 the boot. :cool:

---

### Post by grumble_au on 2008-05-30
I'd like to add my thanks to this post.  I have been trialing out a few different linux distros on my ancient toshiba portege 7220 latptop.  This advice let me install a (x)ubuntu version that worked in anything faster than geological time.  

Note that for 6.06 the network setup works out of the box.  You just need the apt-get install xubuntu-desktop after initial install to get a perfectly usable machine.

The only bugbear is that when you do install the desktop package you need to reinsert the cd.  That's silly but hardly a showstopper.

---

### Post by NastyT23 on 2008-06-04
I've just installed the latest xubuntu (8.04) via the alternate cd on my old desktop pc (hp pavilion 6638). I have a pci network card and when i do the install everything goes fine except when it gets to the configuring network screen. It doesn't seem to detect my pci network card...is there anyway around this? I have 2 of the same desktops with 2 diff pci network cards and neither of them work. Is there a way to get it to recognize my network card? When i go to the graphical network screen it shows eth1 and eth0, and point to point connection. the 2 wired connections say roaming mode enabled...and which one is actually the network card (if it's recognizing it)? Thanks.

---

### Post by Buckoman on 2010-07-19
Hey. After installing xubuntu on my old IBM A20m (127.640 MB RAM), i was almost ready to sell it on eBay. It has no wireless integrated, but can use a wireless card. Anyway, when i plugged in the ethernet cable, the computer didn't recognize it, and i couldn't go online, or recieve crucial first-time updates. Help please?
Running on:
IBM ThinkPad A20m
128MB RAM
Xubuntu 9.10 installed using alternate CD

---

