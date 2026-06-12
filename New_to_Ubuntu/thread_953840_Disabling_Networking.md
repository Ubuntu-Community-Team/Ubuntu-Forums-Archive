---
title: "Disabling Networking"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by AIDS on 2008-10-20
I have a problem that seems almost ironic in nature: I can't seem to get rid of my internet connection.

I am trying to connect two devices (my computer and Nintendo Wii) to a college network through a 5-port wired switch, and my setup and cables all seem to be functional. The problem is that, thanks to restrictions on the college network, I can only have one device using the switch at a time. It is easy enough to switch from the Wii to the computer; as long as the standby connection is disabled, I simply need to turn the system off, and its port goes inactive.

The issue arises when going from the computer to my Wii console. I want to disable networking so that my computer's port goes inactive, thus allowing the Wii to get online. I thought this would be simple enough. I expected that all I had to do was right-click on the Network Manager icon that's conveniently attached to the panel at the top of my screen and uncheck the "Enable Networking" option.

Much to my surprise and dismay, the port on my switch remained active. I did some research on why this might be happening, and discovered that, for whatever reason, the Network Manager does not disable IPv6, even when you uncheck the networking option. So I went into /etc/modprobe.d/blacklist and blacklisted IPv6 there, rebooted my system, yet was still unable to shut down my connection completely. I then tried going into /etc/modprobe.d/aliases and turned off IPv6 through that file, instead. But when I rebooted the system, the problem still prevailed.

I'm guessing there is probably something beyond the IPv6 that also still has access to my wired connection, but I'm not sure what else to try at this point. The ideal solution would be to somehow configure Network Manager to truly and completely shut down the network connection when I tell it to, although if there are other things I can disable that wouldn't require constantly rebooting my computer (or things I could disable that try to access the network that I simply don't need at all), I'm open to that, too.

I basically want the connection to act as if there were no wire plugged into the computer's ethernet port at all. And I realize I could just unplug the wire, but I'd much rather find a software-level solution. That will save me a lot of wrestling with inconveniently-placed hardware and the trouble of constantly power-cycling the switch.

Thank you.

---

### Post by Mark_in_Hollywood on 2008-10-20
Open System/Administration/Network

un-check the wireless or network icon

please mark this thread as solved if this works. Thnx.

---

### Post by namegame on 2008-10-20
try: sudo ifconfig eth0 down

Instead of eth0 use whatever your ethernet device is named. I think eth0 is default though.

Maybe the more experience people know a better/more efficient way.

When you want to use the ethernet again you will need:
sudo ifconfig eth0 up

---

### Post by AIDS on 2008-10-20
Thanks for the speedy responses, but neither of those seemed to work.

I went into System/Administration/Network, created a fake, random IP address because it wouldn't let me just uncheck the wired connection while the system was set to roaming, then went and unchecked the box. It caused me to get the same result as simply right-clicking and then unchecking the "Networking Enabled" option.

I used:

```
sudo ifconfig eth0 down
```

in my command terminal, and that took away the option to use my ethernet port (which I am pretty sure has retained its default name of eth0) for a split second... and then the option came right back, and the computer automatically reconnected to the network using it. During this whole process, the light on my switch stayed completely active.

Any other ideas? This ethernet port just won't die!

---

### Post by aeiah on 2008-10-20
have you tried:
```

sudo /etc/init.d/networking stop
```


perhaps also ```

sudo /etc/init.d/NetworkManager stop
```
too. just replace stop with start to get it back on.

incidentally, have you considered using a router, or using your pc as a router to mask the IPs (NAT) so college think you've just got the one device?

---

### Post by AIDS on 2008-10-20
Well, I tried both of those commands. The first told me that it was deconfiguring the network interfaces, but did not appear to have any effect whatsoever on the network. It didn't even disconnect me from the internet.

The next command simply informed me that the command I entered could not be found.

A router would be a good idea, but unfortunately, we are not allowed to have them on the campus network. I swear, this network is out to make our lives as miserable as possible. I wouldn't be having any of these problems in the first place if my Wii could access the wireless, but that isn't even possible here. As for configuring my computer as a router, I simply lack the hardware and funding at this point in time to actually use that type of setup.

My internet connection seems to have found the secret to immortality.

---

