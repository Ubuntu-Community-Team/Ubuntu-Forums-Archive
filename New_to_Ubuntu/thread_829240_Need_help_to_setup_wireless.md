---
title: "Need help to setup wireless"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-14
Hello, I think i already configured my wireless but i still fail to connect to internet. My router is set up with WPA Personal using TKIP encryption. I think i've entered the right password but still unable to connect. Can someone guide me through this

aznan@aznan-laptop:~$ lspci | grep Wireless
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by ConMan318 on 2008-06-14
Since your card is recognized, I would recommend switching from Network Manager to Wicd.  It makes it extremely easy to get connected wirelessly.  A lot people use Wicd because it is so difficult to get a working wireless connection with Network Manager.

If you want to try it, you'll have to add it through a 3rd party repo from Synaptic.  In Synaptic, go to Settings > Repositories > 3rd Party Software > Add.  Then enter in
```

deb http://apt.wicd.net hardy extras

```

If you aren't using Hardy, change the hardy part to gutsy or whatever you are using.  Then just click reload and search "wicd" and install it.

If you are dead-set on keeping Network Manager (installing Wicd will delete it), I can't really help you since I tried for about a week to get wireless through the command line/Network Manager and failed.

Good luck.

---

### Post by sancho panza on 2008-06-14
Are you able to access the router from ur laptop? If you can, then the problem is with the router, you may need to power cycle your modem/router. If not, try to see if you can access the internet by connecting to the router via ethernet cable. If these work, its an issue with the wireless setup. You can edit the wireless settings by right-clicking the network icon in the notification area.

Cheers!

---

### Post by wariskampar on 2008-06-14
@ConMan318: for now, i would restraint to install additional software/package because I strongly believe there are solution w/o resorting to additional package. Additionally, i can still connect using Ethernet. However, if this problem persist, i will no hesitate to try your suggestion.
@sancho panza: yes, i can access internet using Ethernet.

---

### Post by ConMan318 on 2008-06-14
In that case, you could try the instructions this thread:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

They are instructions for connecting from the command line.  I tried them and got close to getting connected, but never quite made it.  Maybe you will have better luck.

---

### Post by wariskampar on 2008-06-14
@ConMan318; after looking at wicd webpage, i think i will give it a try. However, since you said that Network Manager will be "erase" afterward, i'm curious about my initial setting. I use static ip instead of dhcp because it helps boosting my torrent d/load. so, if i d/load wicd, is all the setting lost?

---

### Post by wariskampar on 2008-06-14
Hello, i already install wicd. i still unable to connect wirelessly and on top of that 2 new problems appear:
1) if i unplug ethernet, i will lose connection when reconnect the cable
2) after reboot, no wicd window appear when i click on it. 
May i know how you setup your Wicd?

---

### Post by ConMan318 on 2008-06-14
> 
1) if i unplug ethernet, i will lose connection when reconnect the cable

To my knowledge, Wicd will not automatically connect, though I haven't tried to set it to do so.  Thus, if you unplug your ethernet cord, to reconnect you will have to select 'connect' in Wicd after plugging it back in.

> 
2) after reboot, no wicd window appear when i click on it.

What exactly are you clicking on?  By this I mean is it a taskbar shortcut icon or in Apps > Internet > Wicd?  If you are trying one of those and it won't start up, try running it from the command line, with Alt-F2 (type wicd in and double-click the search result), or making a custom launcher.  The command to start it is
```

/opt/wicd/gui.py

```

If that doesn't start it, I'd try rebooting one more time and then trying the command again, though it is quite odd that it won't open the Wicd window; I have never had that problem.



As to your previous post, I am not really sure, but I would imagine any settings you changed in Network Manager would, indeed, be lost.  If that is the case, you could try opening Wicd and clicking the little arrow next to the network name and try checking the "use static IP" box and configuring settings there.

---

