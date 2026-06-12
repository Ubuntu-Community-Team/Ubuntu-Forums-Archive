---
title: "[SOLVED] Having problems with Remote Desktop connection"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by MikeBrown on 2008-11-10
I am relatively new to Ubuntu, just installed 8.1 on a computer last night and previous to that I have had very little experience with Ubuntu, so to preface I am a n00b and pretty much need someone to hold my hand through this process. 

I set up a Remote Desktop connection on my Ubuntu computer and did all the steps like I have seen in other posts. I checked all of the "allow others to view/control your desktop" , "require password" and the like. 

I want to connect to the Ubuntu computer from a computer running Windows Vista. I have downloaded and installed tightVNC viewer already on the Vista computer.

I then went to the Ubuntu computer and checked the IP address thru the terminal command "/sbin/ifconfig" which showed my IP address. For reasons of privacy, I will not list it, but it does start out 192.168.... which I have read is the address you are supposed to enter in TightVNC on the other end (the Vista computer). 

When I try to log onto the remote desktop connection, it tries to connect for a few seconds, then gives me an error every time. 

What am I doing wrong? 

I can post screenshots of all the settings if necessary

thanks in advance!

-Mike

---

### Post by echo.whoami on 2008-11-10
it sounds to me that you should open the required ports. Default the port is 5900 so you have to open it in the iptables and then from the router forward the port to the local ip of the pc.

A gui for the iptables is the firestarter which i use and find it very simple even for newbies.

For the router you will have to get in the interface of ther rourer and look for something like nat or ports forwarding...

---

### Post by saj0577 on 2008-11-10
The 192.168 ip doe snot need to be kept that secret as it is your internal ip address for only your network. :) 

You may need to configure your router to allow the ports, in most cases this is not needed as you are accessing a computer from within the network.

Can you post a screenshot of the settings please just so I can see them in front of me.

Thanks
Saj

IF your ip is 192.168.1.x  then use 192.168.1.1 to access your router.
OR 
If your ip is 192.168.0.1 then use 192.168.0.1 to access your router.

---

### Post by bodhi.zazen on 2008-11-10
> **echo.whoami said:**
> it sounds to me that you should open the required ports. Default the port is 5900 so you have to open it in the iptables and then from the router forward the port to the local ip of the pc.

A gui for the iptables is the firestarter which i use and find it very simple even for newbies.

For the router you will have to get in the interface of ther rourer and look for something like nat or ports forwarding...

Well, this is a little misleading as with a default Ubuntu installation iptables is permissive and will not block the connection.

We need more information. Are the Windows computer and the Ubuntu box on the same network ? Are you running a firewall on Windows ?

---

### Post by MikeBrown on 2008-11-10
> **bodhi.zazen said:**
> Well, this is a little misleading as with a default Ubuntu installation iptables is permissive and will not block the connection.

We need more information. Are the Windows computer and the Ubuntu box on the same network ? Are you running a firewall on Windows ?

The two computers are on the same network right this moment, but I wanted to set this up so that if I was on the road I could still remote control my Ubuntu setup from another network. 

I am running a firewall on Vista, which is set at the default settings. 

Screenshots coming soon.

---

### Post by MikeBrown on 2008-11-10
Here are the screens of the windows. 

[IMG]http://i265.photobucket.com/albums/ii226/xtremeleewyte/Terminal.png[/IMG]

[img]http://i265.photobucket.com/albums/ii226/xtremeleewyte/RemoteDesktop1.png[/img]

[img]http://i265.photobucket.com/albums/ii226/xtremeleewyte/RemoteDesktop2.png[/img]

[img]http://i265.photobucket.com/albums/ii226/xtremeleewyte/TightVNC2.jpg[/img]


Hope this is what you need, if not let me know

Thanks!

---

### Post by Coreigh on 2008-11-10
Have you seen this how-to yet?
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")

---

### Post by MikeBrown on 2008-11-10
> **Coreigh said:**
> Have you seen this how-to yet?
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")

Not from that source, but from various posts here on the Ubuntu forum. Yes I have, though somehow I still get the error. Thanks anyway!

---

### Post by bodhi.zazen on 2008-11-10
My guess would be your firewall on Vista. Turn it off and try again.

Sometimes you need to specify the port as well.

ip_address:5900

---

### Post by MikeBrown on 2008-11-10
I turned off my firewall and tried connecting to the 192.168... connection. 

Could it be that I'm not trying the right IP? 

I went to whatsmyip.org on the Ubuntu computer and it is showing a different number than any that are showing up in the terminal.

EDIT: I also checked the exceptions on my firewall, and TightVNC is already listed. Didn't know if that would make a difference.
I'll try to connect to the Vista computer from the Ubuntu and see if that works.

---

### Post by bodhi.zazen on 2008-11-10
If you are connection in the LAN, use the 192.168.x.y of the Ubuntu box.

If you are connecting over the Internet, use the Public IP address and configure your router to forward port 5900 to your Ubuntu box.

---

### Post by MikeBrown on 2008-11-10
I have resolved the problem, though in a method that isn't exactly the simplest, but works anyway. 

I took the most recent Ubuntu install disc and installed a partition to run in Windows. Again, not being familiar with Ubuntu, I figured that the new partition would run in a window in Vista, but I guess I somehow created a dual-boot partition to run either Vista or Ubuntu. So thanks to all of you that replied to my query but I have worked out my own solution. 

-Mike

---

