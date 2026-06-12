---
title: "Firefox- how to disable default Browse offline mode."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-02
When ever i start my firefox its starting in borwse offline mode.

How to change this.

---

### Post by EXCiD3 on 2008-06-02
Are you connected to the internet? I've read that this is caused when you are NOT using NetworkManager. This thread talks about the problem fairly extensively: [http://ubuntuforums.org/showthread.php?t=708431](http://ubuntuforums.org/showthread.php?t=708431)

---

### Post by rraj.be on 2008-06-02
I have already installed network manager.

But this is happening for me when ever im starting firefox.

Really anoying.

---

### Post by rraj.be on 2008-06-02
I cant solve this.
any one have some solution for this?

---

### Post by EXCiD3 on 2008-06-02
There is a very long bug report of this filed here: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889)

Looks like this is probably your best option for a fix:
> [PearZoo]("https://bugs.launchpad.net/%7Epeter4")          wrote     on 2008-05-29:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889/comments/129")                            [FONT=monospace]Best thing I even did was remove network-manager and install WiCD. There is just no comparison, network-manager has always, in my opinion been the poor cousin of WicCD.
 Install instructions here:
 [http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)
 Good luck
[/FONT]

---

### Post by rraj.be on 2008-06-02
I will try it.

But is there any problem because of removing network manager

---

### Post by EXCiD3 on 2008-06-02
It seems that Network Manager IS the problem. WICD is just a replacement for it and it has the same capabilities and IMHO works better. I would recommend it over and above Network Manager every time if you are experiencing any problems with Network Manager.

---

### Post by rraj.be on 2008-06-02
k i will try now.

Could you help me in configuring my Evolutionor thunderbird.

I already have a thread  but no solution yet.

[http://ubuntuforums.org/showthread.php?t=816655]("http://ubuntuforums.org/showthread.php?t=816655")

please help me if you can

---

### Post by freund on 2008-06-03
Find "browser.offline-apps.notify" in the "about:config" method and set it to false.

See discussion on rational at [http://forums.mozillazine.org/viewtopic.php?t=653981](http://forums.mozillazine.org/viewtopic.php?t=653981)

---

### Post by freund on 2008-06-03
sorry this doesn't work on a continuous bases for me.

---

### Post by rraj.be on 2008-06-03
Is there any other solved solution for this problem

---

### Post by aparigraha on 2008-10-04
[The XLNT Firefox Add-On!!]("https://addons.mozilla.org/en-US/firefox/addon/8502")

---

### Post by lswb on 2008-10-04
The problem is indeed because of network manager. Fortunately the firefox developers went out of their way IMHO to help: open about:config and set:

toolkit.networkmanager.disable

to "true"

This is not available in the 1st release of firefox 3.0, you need 3.0.2 or higher I believe.

Unfortunately, other apps like evolution and pidgin AFAIK are still hampered by this networkmanager flaw.

---

### Post by ellalan on 2008-10-08
Go to Terminal and type: gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf

Then find the lines(there are 3): <allow send-interface.....
change the word "allow" to "deny". This worked for me. HTH.

---

### Post by OMA2k on 2008-10-12
Setting "toolkit.networkmanager.disable" to "true", as explained by lswb, worked for me! Now local web server applications work even if there's not an Internet connection.

Thanks a lot, lswb!

---

### Post by Kar.ma on 2009-02-14
> **lswb said:**
> [...] open about:config and set:

toolkit.networkmanager.disable

to "true"

[...]
This worked fine for me, thanks. I have two internet connections, and I switch from one to the other one sometimes. If I'm connected via cable Firefox knows I'm online, while the Bluetooth connection had the "offline mode" problem,  now fixed thanks to lswb.

---

### Post by nechal on 2009-03-18
hello ubuntu people, I had the same proble in my firefox as I always get the same message at the beggining and it's very painfull to go each time and swap to online mode.
hopefully, while looking around in forums, I found the solution here: [http://yellosoft.us/index.php?id=88]("http://yellosoft.us/index.php?id=88")
you just need to download the extension into your desktop, open firefox window, drag and drop the extension into it.
the next step is enjoying the online mode and saving too many minutes in your life deactivating the offline mode.
FYI: this extension worked fine for me.

---

### Post by fornix on 2009-04-26
Hey, can anyone do the following and confirm whether it solves the problem
Disable networkmanager altogether

```
System -> Preferences -> Startup Applications
Uncheck Network Manager
```

I use a pppoe connection and connect using pppoe-start.

---

### Post by fornix on 2009-04-28
I managed to solve (Solve?) the problem in firefox and pidgin by kicking off NetworkManager altogether and using the good old method. The steps I followed are as follows:

1. Disable the Network manager applet
```
System -> Preferences -> Startup Applications
Uncheck Network Manager
```

2. Disable the NetworkManager init script from starting at boot time.
For this, I used a utility called sysvconfig. sysvconfig is a ncurses based simple application which allows us to disable/enable boot scripts easily.
```
$ sudo apt-get install sysvconfig
```
Start the application by 
```
$ sudo sysvconfig
```
Uncheck NetworkManager. Save and exit.
Other ways to disable the boot scripts can be found here [https://help.ubuntu.com/community/UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

3. Edit the file /etc/network/interfaces with information about my interface (eth0)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.20.51.21
	netmask 255.255.255.0
	network 10.20.51.0
	broadcast 10.20.51.255
```

4. Restart the computer and you're done!!

PS. I use static IP configuration instead of DHCP and I connect to internet via pppoe based connection and use rp-pppoe package for connecting.
So I just use $ pppoe-start to start my connection.
If you are using a DHCP based connection, your configuration should be much simpler - the interfaces file should only contain the line 
```
iface eth0 inet dhcp
```

---

### Post by fetuspuppet on 2010-07-09
```
root@ubuntu:~# apt-get install sysvconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sysvconfig is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sysvinit-utils


```

Looks like sysvconfig has been superseded... But this one should do the same thing. :popcorn:

---

### Post by Klevn on 2011-02-03
PROBLEM SOLVED HERE:  Easiest best solution, I think

> How to Disable Firefox Offline Mode 	PDF 	Print 	E-mail
Written by Doug Bierer   
Thursday, 31 December 2009 13:10

It seems whenever I upgrade my version of Firefox I keep getting this doggoned message:

 "Unable to connect: Firefox is in offline mode"

The reason for this is that whenever the WiFi or mobile broadband connection gets dropped (out of range, poor reception, etc.), Firefox gets "notified" by its network manager component.  The default behavior is to go into "offline mode".  How WINDOWS like!!!  (i.e. how IRRITATING!!!)

Solution:

   1. Open a browser window or tab using "about:config" for your URI
   2. Locate "browser.offline"
   3. Double click to set the parameter at the right to "false"
   4. Locate "browser.offline-apps.notify"
   5. Double  click to set the parameter at the right to "false"
   6. Close the window or tab

Your browser should now default to "online" mode by default.  Also, when you lose your network connection, it should NOT automatically revert to "offline" mode.

from: [http://joomla.unlikelysource.com/index.php/misc-tutorials-category/40-howto-firefox-offline]("http://joomla.unlikelysource.com/index.php/misc-tutorials-category/40-howto-firefox-offline")

---

