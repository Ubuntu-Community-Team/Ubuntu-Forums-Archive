---
title: "Ubuntu 15.10 - I cannot get on-line !!"
date: 2016-01-17
forum: New to Ubuntu
---

### Post by joan7 on 2016-01-17
Hi everybody, 
after using Suse for over 10yrs I have had bother with the latest distro, so I have switched to Ubuntu which I use on my Litecoin mining rig.
I have a clean install on a new 1Tb harddrive of Ubuntu 15.10 AMD64. 
The installation did take some time, which caused me a bit of concern. It seemed to stick at some language packs ...
Anyway, my machine booted up OK and everything seems to be there, except that I cannot get on line.
I see from the notifier on the top rh corner that I do have a connection ; Hard wire connection 1
I cannot find a network manager like in Suse, but the Toolbox options let me see my network configuration, which I must say does not look like a cause for great concern. I cannot see any obvious faults. I also cannot get access to my firewalls, so I cannot see if they are enabled or not.
Anybody any ideas ?
Should I re-install ?

---

### Post by cogier2 on 2016-01-17
What machine are you using? If you have wifi does that work?
In Terminal run **ifconfig **and post the output here. 
Clicking on the icon should get you to the Network Manager.

---

### Post by joan7 on 2016-01-17
Cogier2,
thank you for your reply.
I have just swapped over hard-drives again, and i ran ipconfig like you suggested.
Output looked fine, so i opened up my browser, and low-and-behold !
It opened up, and took me to my homepage !
So i am now replying to you using my freshly installed Ubuntu 15.10 system.
OK, I do not know what was going on, but i spent the best part of 4 hrs installing the system.
maybe the hard-drive just wanted a rest, before it swung into action ?
Hopefully I can now get on with the rest of my software installation.

I appreciate your help. thanks.
-J

---

### Post by grahammechanical on 2016-01-17
Just a small point.

> I cannot find a network manager like in Suse,

There is one. We access it from the Network manager icon in the top panel. In the past there were 2 or 3 or even 4 different ways to access the same system utilities. That has been very much reduced in Ubuntu.

From the Network icon menu, do you have WiFi enabled? If you do, do you see a list of wireless access points? That will tell you if the WiFi adapter is switched on and has a driver. Select your wireless access point and a dialog will appear where you can enter the wireless passphrase or key to authenticate the connection.

In some case we may need to go to system settings>software & updates>additional drivers tab and install a wireless driver. We need to be connected to the internet (wired connection) and allow time for the utility to find some drivers. This is only necessary for when Linux does not have a driver module for our WiFI adapter.

Regards

---

### Post by ajgreeny on 2016-01-17
Good news!  And welcome to the forums.

Can you please mark this thread as SOLVED from the Thread Tools menu at the top.  It may help others with similar problems who are searching for answers.

---

