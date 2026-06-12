---
title: "Network / Scripts / Startup / Run Levels Query"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by counciller on 2014-08-23
Hello, 

I decided to revisit Ubuntu and I am more confused than ever - I am not a Linux guru and despite hours of trawling the net I haven't found the sure to be simple information I am after. 

I don't know what is controlling my network interfaces - I configured them on installation using the GUI - I see references to Network Manager and people trying to disable it on the net (no idea what that is) - but I look in my file version and it doesn't even contain a eth0 statement.

Am I even using NetworkManager? what is controlling my network? 

I just want to know how to tell what program's are controlling my network addressing and routing (as my manual changes keep getting over-written and I have no idea what is doing it)

How do I tell what programs are responsible for starting up my GUI on start up? I looked in what I thought was the standard start-up script locations the rc.1 through to rc.6 folders - but nothing in there is starting my GUI--- so how do I tell what is responsible for starting programs/scripts on my system when I can't even see what is calling them? -- and then how can I add a script to it?

All I am trying to do is set eth0 route to a higher metric than the wlan0 route - nothing I do sticks and I don't understand why. Something keeps overwriting my settings and I have no idea what.

I then realised I don't understand how Ubuntu is starting my GUI environment or anything for that matter and I would like to learn how it works. 

Honestly what am I missing?, surely it shouldn't be this hard ... 

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

Thanks guys in advance to any light you can shed on this for me

---

### Post by TheFu on 2014-08-23
Start here [http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) to get a translation for Windows users. 
It will really help.

Most of your questions are NOT ubuntu specific.  The GUI is NOT the OS. It is just another program on the system.

---

### Post by steeldriver on 2014-08-23
In the standard Ubuntu Desktop version, the X-server (GUI) and its user-sessions are started by a *display manager* called **lightdm**, which in turn is started by the upstart mechanism - through a configuration file at /etc/init/lightdm.conf

The standard Desktop editions use **network-manager** for network interfaces - this is also started via upstart, using the configuration file /etc/init/network-manager.conf

If you explain a bit more exactly what you are trying to do I'm sure someone will be able to point you in the right direction. By default, the network-manager only brings up one interface at a time - so if you are trying to do more complex multi-interface routing with metrics you may need to revert to the older ifupdown/**networking** service (which runs, but only manages the loopback interface by default). If you do that you will probably want to disable network-manager so that they are not in conflict.

---

### Post by JKyleOKC on 2014-08-23
> **counciller said:**
> Am I even using NetworkManager? what is controlling my network? 

I just want to know how to tell what program's are controlling my network addressing and routing (as my manual changes keep getting over-written and I have no idea what is doing it)

How do I tell what programs are responsible for starting up my GUI on start up? I looked in what I thought was the standard start-up script locations the rc.1 through to rc.6 folders - but nothing in there is starting my GUI--- so how do I tell what is responsible for starting programs/scripts on my system when I can't even see what is calling them? -- and then how can I add a script to it?

All I am trying to do is set eth0 route to a higher metric than the wlan0 route - nothing I do sticks and I don't understand why. Something keeps overwriting my settings and I have no idea what.

I then realised I don't understand how Ubuntu is starting my GUI environment or anything for that matter and I would like to learn how it works. 

Honestly what am I missing?, surely it shouldn't be this hard ... 

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

Thanks guys in advance to any light you can shed on this for meHaving gone this exact same route several years ago after quite a few years using a RedHat-based system, I understand your problem. TheFu and steeldriver are both extremely competent in this area but I have the feeling that they may be assuming that you're coming from Windows; I suspect that you're coming from a non-Debian but Linux environment.

The *buntu family of distros no longer use the rc*.d boot system nor do they pay much, if any, attention to runlevels. Instead they use "upstart," which is an event-driven approach that lends itself to multi-thread parallel processing where possible. It's also quite confusing to one who's steeped in the rc*.d approach! And this isn't really relevant to the question of your network settings getting overwritten, anyway.

Several years ago, Ubuntu moved away from the /etc/network/interfaces system that initializes your network settings, in favor of a GUI-based system called Network Manager that does all the configuration without requiring anything entered at a command line. More recently, that system has adopted use of a program called dnsmasq that silently modifies your settings based on responses to dns queries. I strongly suspect that this is what's causing your problems.

It's possible to disable these simplifications and go back to the older way of configuring the network interfaces; I'm running that way right now. However you are using Ubuntu 14.04 while I'm still on Xubuntu 12.04.4, and these different flavors have some major differences in how their configurations are maintained. Thus I can't give you much detailed guidance in making the changes. Search the forums for "Network Manager" and also (separately) for "dnsmasq" and you should find much more detailed guidance.

Specifically, I don't know what effect disabling these settings will have on the Unity interface that's now the default for Ubuntu itself. So long as dnsmasq is running in its default configuration, though, any changes you make in the "interfaces" file or with the route command will be overwritten almost immediately...

Hope this helps! If you're feeling really experimental, I can tell you how I disabled them -- but it might give you worse problems than you already have!

---

