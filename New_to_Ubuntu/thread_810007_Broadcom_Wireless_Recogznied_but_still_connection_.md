---
title: "Broadcom Wireless Recogznied but still connection issues..."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by MikeRaines on 2008-05-27
Hi all,

I have been debugging and working to get my broadcom wireless card recognized for the last night or so. After posting here I got a quick link to [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) which was a nice walk-through that got my wireless card drivers installed and working.

Now after hours of doing that I am having one last bit of trouble.

I have tried both command line attempts to get on my wireless
```

mike@icarus:~$ sudo ifconfig wlan0 down
[sudo] password for mike: 
mike@icarus:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:70:f5:11
Sending on   LPF/wlan0/00:1a:73:70:f5:11
Sending on   Socket/fallback
mike@icarus:~$ sudo ifconfig wlan0 up
mike@icarus:~$ sudo iwconfig wlan0 essid "N7AC4"
mike@icarus:~$ sudo iwconfig wlan0 key 18016F42B3
mike@icarus:~$ sudo iwconfig wlan0 mode Moderated
Error for wireless request "Set Mode" (8B06) :
    invalid argument "Moderated".
mike@icarus:~$ sudo iwconfig wlan0 mode Managed
mike@icarus:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:70:f5:11
Sending on   LPF/wlan0/00:1a:73:70:f5:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Along with using the GUI.

In both the GUI and
```

iwlist scan

```
My wireless network is correctly displayed, but when I attempt to connect to it, no dice.

Any help would be greatly appreciated, I am tired of having to hook up to a cable.

---

### Post by spiderbatdad on 2008-05-27
Do you have the line "ndiswrapper" in the file /etc/modules? If not please add and reboot.

---

### Post by MikeRaines on 2008-05-27
Yes, here is my current /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper

```

Any other ideas? It's frustrating being able to see the wireless networks but not being able to connect to them.

---

### Post by spiderbatdad on 2008-05-27
Just not sure. I have a similar problem on an hp machine. I have to run these two commands in order```
sudo ifdown wlan0
sudo dhclient wlan0
```That get me an address then internet is fine, but  lease eventually expires.
My cisco aironet card works fantastically out-of-the-box.

It is obviously a driver config problem somewhere. Sorry I couldnt be of more help. you can always try to modprobe again and run depmod at any time.

---

### Post by seagullplayer77 on 2008-05-27
I was fighting a similar battle with my Atheros card over the Memorial Day weekend (Grr...). Anyway, lspci would detect my wireless card and the driver and hardware were both listed as working by ndiswrapper and I could even detect wireless networks--signal strenghts, SSIDs, encryption types, the whole nine yards--I just couldn't connect to 'em. I'm not sure if this is what got it all working, but I've gotten my wireless up and running for three days straight using this process.

If you haven't already, download Wicd. I don't believe it's a standard Synaptic package, but you can follow the directions the directions here and get the package installed:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Btw, Wicd will install any other network management tools you have (Network Manager, WiFi Radar, etc.), just so you're aware.

After you've got Wicd installed, you can bring up a tray icon by running /opt/wicd/tray.py. If this solution ends up working, you can add that same command into Sessions and the applet'll start when you log in. 

Anyway, I was never able to get Wicd to work until I ran these two commands:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 00:00:00:00:00:00

If your wireless interface is named something other than "wlan0," you'll obviously have to change that line. 00:00:00:00:00:00 is your MAC address, which I believe you can obtain by running:

dhclient wlan0

Obviously, you'll have to change wlan0 to whatever your wireless interface is named again. 

After you run the two ifconfigs, try connecting to a wireless network using Wicd. If that doesn't work, I'll try to help, but I can't make any promises--I'm not a Ubuntu god :-)!

In case you were interested in looking at my original thread, you can check it out here:

[http://ubuntuforums.org/showthread.php?t=805856](http://ubuntuforums.org/showthread.php?t=805856)

Not sure that it'll help you any, but ya never know. Good luck!

---

### Post by MikeRaines on 2008-05-27
I appreciate the post but it didnt do much good.

Installing Wicp did effectivlly kill my hardwire connection though, and did nothing to help my wlan0.

I had to manually boot my hardwire connection through command line to fix this
```

sudo dhclient eth0

```
After that I was able to uninstall Wicp package and redownload network manager.

Thanks for the try though.

Any other ideas?

I can see all the networks but they just wont accept the connection :(

---

### Post by Bill magee on 2008-05-27
Mike, have you gone into your network connection window and clicked on the little circle to the left of your connection name? You can't get the connection until you click it.

Cheers,
Bill

---

### Post by seagullplayer77 on 2008-05-27
Hmm...sad to say, but I had the same exact problem many a time myself. I tried installing Wicd easily three or four times and it never did anything (except kill my hardwire!), and I ended up uninstalling it and reinstalling Network Manager. Then, by some miracle, Wicd started working perfectly, just as long as I ran those two ifconfig commands first. Gotta love Linux, right :-)?

There were a few other ideas on that thread I linked to, but I'm not sure that any of 'em will help you. I suppose it couldn't hurt, though. If you haven't tried any of those, I'd give it a shot.

Oh, and sorry that Wicd took out your wired connection. I hadn't really anticipated that happening to someone else! Glad you got THAT fixed, though.

---

### Post by rpwdh on 2008-05-27
My laptop had the same problem. I hooked up (wired) to my router and ran System Update. It recognized my Broadcom and went to get the firmware.

I hope you get it going!

---

### Post by MikeRaines on 2008-05-28
> **rpwdh said:**
> My laptop had the same problem. I hooked up (wired) to my router and ran System Update. It recognized my Broadcom and went to get the firmware.

I hope you get it going!

I appreciate it. I have moved my laptop to a new area to test if it was just my router denying my connection. This turns out is not the case. Any other suggestions?

---

### Post by gali98 on 2008-05-28
at the risk of sounding stupid, you do have the following lines in /etc/network/interfaces:

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid your_essid (replace this with yours obviously)


then just run
 
sudo /etc/init.d/networking restart

That helps sometimes. I hope this helps you and doesn't make me sound stupid.
Kory

---

### Post by MikeRaines on 2008-05-28
iface nor inet are not recognized as valid commands.

---

### Post by spiderbatdad on 2008-05-28
> **MikeRaines said:**
> iface nor inet are not recognized as valid commands.

I believe a slight miscommunication occurred:

> do have the following lines in /etc/network/interfaces:

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid your_essid (replace this with yours obviously)


---

### Post by MikeRaines on 2008-05-28
> **spiderbatdad said:**
> I believe a slight miscommunication occurred:

Haha ya I see that now.

BUT I have managed to get my wlan0 connected! But the problems continue!

Here is how I managed to fix it. I am not sure why this works any different from what I was doing before I just switched up the order of some of the commands.

```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig essid "mrn02" //I am trying a different connection from my home one
sudo iwconfig key ********
sudo iwconfig mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

The only thing different about this procedure and what I was doing before is **sudo ifconfig wlan0 up** is not run untill the essid key and mode are set.

After doing it this way I received an offer from the router and bound successfully.

**The Automatic Updater Works and Can Download Files!**
But the issue now is I cannot ping websites via command line and firebox browses as if it is disconnected from the internet.

Any Suggestions?

---

### Post by spiderbatdad on 2008-05-28
I was going to ask you whether the network was seccurred, but I thought no, that's a dumb question....
Have you installed the wpasupplicant? The tutorial you followed uses the program: ENABLED=0 /etc/wpasupplicant thingy.

---

### Post by MikeRaines on 2008-05-28
Ya, I just ran

```

sudo apt-get install wpasupplicant

```
and it tells me I have the newest version already.

And just to make sure my wifi is actually working and not an illusion I just ran.
```

sudo apt-get install amarok

```
and it got and is currentlly downloading amarok, but still no browsing or pinging available.

---

### Post by lswest on 2008-05-28
see if disabling ipv6 in firefox helps you.  Do ```
about:config
``` in the address bar of firefox and then find network.dns.disableIPv6 and set it to "true".  If that works, then disable ipv6 for Ubuntu (not sure how to do so, but someone else is bound to know).

---

### Post by MikeRaines on 2008-05-28
Thanks for the try, but no dice.

IPv6 Apparentlly isnt the issue.

---

### Post by spiderbatdad on 2008-05-28
maybe try turning off ipv6 in /etc/modprobe.d/aliases

```
locate the line:

alias net-pf-10 ipv6

with:

alias net-pf-10 off
```

Or, make it look like this:
```
#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off 
```

Reboot.

---

### Post by MikeRaines on 2008-05-28
> **spiderbatdad said:**
> maybe try turning off ipv6 in /etc/modprobe.d/aliases

```
locate the line:

alias net-pf-10 ipv6

with:

alias net-pf-10 off
```

Or, make it look like this:
```
#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off 
```

Reboot.


This also did not work. I am assuming IPv6 is not the issue here. I just downloaded some updates and what not through command line but still no browsing or pinging available.

This switch to Ubuntu has been rather frustrating. :(

---

### Post by spiderbatdad on 2008-05-28
You could always email broadcom and express that you are disappointed they did not supply drivers or support to the opensource community. Email your pc manufacturer as well and express your disappointment they use hardware that doesn't provide support or drivers to opensource software. 
My IBM thinkpad t-30 has always worked excellently....wireless flawlessly-out-of-the-box.

It may sound lame, but you would not be alone in expressing disappointment to the manufacturers. The more feedback they get, the more likely things are to improve. Meanwhile shop appropriately.

---

### Post by rpwdh on 2008-05-28
> **MikeRaines said:**
> I appreciate it. I have moved my laptop to a new area to test if it was just my router denying my connection. This turns out is not the case. Any other suggestions?

Sorry, I'm just a n00b myself. Maybe I just got lucky. :confused:

---

