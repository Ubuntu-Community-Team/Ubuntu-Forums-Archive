---
title: "[python] ifconfig not persistent"
date: 2011-05-18
forum: Programming Talk
---

### Post by feisty01 on 2011-05-18
hello, I'm newbie in python language and to begin I decided to create a script which take agrs : interface, ip and netmask in order to configure automaticaly networks interfaces. 

To push on system I use os.system(str) where 'str' is the string below : ifconfig eth0 192.168.1.101 netmask 255.255.255.0  

It works but only few minutes. After 10 minutes, the interface go back to it initial statement AUTO and I don't understand why. 
I also try use popen method unfortunately with th same results. 

Any ideas? thanks

---

### Post by Tony Flury on 2011-05-18
Possibly due to the fact that os.system creates a new shell which then closes.
Could it be that when the new shell closes the changes revert ?

You might need to find a library to use to make your change.

---

### Post by DaithiF on 2011-05-18
Probably its Network Manager doing its thing and managing the connection for you -- ie. overwriting your manually set config with what it thinks the settings should be.  Short of disabling network manager, i'm not sure theres a way to have NM respect what you do at the command line with ifconfig.

---

