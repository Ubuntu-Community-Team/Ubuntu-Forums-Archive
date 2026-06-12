---
title: "[Shell Script] WUPE - Easily connect to networks"
date: 2008-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by aflog on 2008-01-16
I have written a script based of [THIS]("http://ubuntuforums.org/showthread.php?t=571188") tutorial... because i think the code is too long and needs to be easier. 

At the moment it ONLY SUPPORTS **UNENCRYPTED CONNECTIONS**...
If people like it, i can add support for more connection types.
It also has the ability to replace drivers being used by the network interface (assuming they are already installed). 

I have tested using my wireless LAN and it works perfectly using the -cu command. (i have a D-Link DWL-G510 network card with a Belkin 54g router).

Installation:
1. Download and un-tar the archive.
2. Copy the script "wupe" into the /usr/bin/ folder

Help:
Once installed open up a terminal window (anywhere) and type:
> wupe -h

Example:
This is how I connect (RESULTS/METHODS MAY VARY)
> wupe -r rt61pci ndiswrapper
wupe -cu wlan0 "belkin54g"

I have tested on using wlan0 however im not sure if it will work with eth0, eth1 etc. So please if you use it please post your findings here!

Any suggestions or comments can be posted here or PM me.

Thanks for your time
Jayden

PS: Wupe stands for (**W**ay **U**p **P**ast **E**verything)

---

### Post by aflog on 2008-01-16
@mods... if this post in the wrong place, please move it :D

Jayden

---

### Post by NullHead on 2008-01-16
Nice work there. :popcorn:

---

