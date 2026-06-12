---
title: "Help, Netgear WG111 on 8.04"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Linux_Noobie on 2008-08-08
I have no clue or internet on my PC.(I am on my sisters) I figured it would work on the Newest but i guess not How do i set it up. 

Step by Step please.

---

### Post by tarps87 on 2008-08-08
If i understand rightly it is a usb adapter?
There is a program called NDISWrapper, if you download the .deb file and install it on your laptop. Then look in the windows drivers for a file that ends with .inf, if there is a choice use the xp driver first.
The NDISWrapper.deb file can be found here:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

You should only need the file:
ndiswrapper-common_1.52-1ubuntu1_all.deb
but im not using ubuntu so can test it.
This should work but not all devices are supported yet.
I hope this helps

---

### Post by Linux_Noobie on 2008-08-08
did that just found out v3 has only an exe file.. No Direct drivers.

---

### Post by Crafty Kisses on 2008-08-08
You're definitely going to have to use a Ndiswrapper.

I've setup tons of Ndiswrappers so I'm gonna try to help you right now.

First off with Netgear you'd probably want to install the Windows XP drivers.

```
ndiswrapper -i netwg111.inf /*install the windows xp driver*
```
Then you want to check if the Ndiswrapper installed correctly:
```
ndiswrapper -l
```
Then do the following:
```
modprobe ndiswrapper
``` 
If it works you should see the light.
```
ndiswrapper -m
```
You then want to boot it as a module, you're gonna have to for Netgear.
```
iwconfig wlan0
```
Look over your settings make sure everything is cool, then ```
iwconfig wlan0 essid ESSID key restricted (whatever it is here)
```
After all that, do this one last thing:
```
dhcpclient wlan0
```
Then you should be set, I have yet to use a Netgear wireless adapter but this is one way it worked for some people, and it might work for you.

If you have any troubles at all feel free to contact me, I've setup tons and tons of Ndiswrappers so I can help you pretty good I think, but again hopefully this helps.

---

