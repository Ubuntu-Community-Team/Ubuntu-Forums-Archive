---
title: "New to networking"
date: 2021-11-12
forum: New to Ubuntu
---

### Post by awill10 on 2021-11-12
Is there a simple process to follow when connecting a wired and wireless network with Ubuntu. There are many ways to do this but I'm just looking for simple steps for both.

---

### Post by ajgreeny on 2021-11-12
Are you having problems connecting in either way or have you not even tried to do so; If using an ethernet cable the system will normally find the connection and work immediately.

If using wireless a lot will depend on the wireless network hardware in your computer which, of course, we know nothing about.
For a start have a read through the pages you see linked to at [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

To give us more background open a terminal and use command ```
inxi -Fzx
``` exactly as I have shown it and then copy paste the output back here.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by grahammechanical on 2021-11-12
Ubuntu comes with a desktop guide. In the side panel it is represented by a blue circle with a white question mark. It has a section called Network, Web and Email. It is detailed. To connect wirelessly you will need to know the name of your wireless router/hub and its password.

Here is a link to an online version of the desktop guide for Ubuntu 20.04.

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

Regards

---

### Post by TheFu on 2021-11-12
First, only enable 1 or the other. For someone really new, never enable with wifi and wired connections.

It should just connect to any wired connection, assuming there is a router and a DHCP server correctly configured.

For wifi, there is a network button, usually in the upper right-hand corner to click where the SSID and PSK are entered. I think at the first connection, it will ask if this is per-user or system-wide.  If you choose per-userid, then it will only connect to wifi AFTER a login. This means you can't connect from some other system before physically logging in - which can be a hassle as you learn more about Linux. Again, this assumes there is a wifi-router, the SSID and PSK (pre-shared key) and a DHCP server is setup and working.

It is all pretty easy.

Of course, if there are issues with the router or DHCP or wifi, then this won't work.  If other computers on the network are connecting and working, then Linux/Ubuntu should work too.

If either or both aren't working (wifi/ethernet), then it can be something you've done by mistake during the setup. It could be really new hardware or incorrect drivers.  I can assure you that happens very seldom, but it does happen (and likely will always happen) from time to time.
**inxi -Nxxxz** will gather all the network information, if inxi is available. It isn't part of a new install, unfortunately.
**lshw -sanitize -C network** will gather some network information, if lshw is available. It isn't part of a new install, unfortunately.
So, that leaves you with complex commands ... 
```
lspci -vk |  egrep --after-context=8 'Ethernet|Network'
lspci     -vk    |    perl     -lne     'print if       /Ethernet|Network/    ..      /^[\w]*$/'
```
either of those commands should provide non-USB network device information. Spacing is very important in the pattern-match parts. Don't worry too much about spaces elsewhere in the commands 1 or 50 spaces are the same.

The starting point is to see if the OS knows which device is available (network device) and if a driver is being loaded.  Fixing wired ethernet is usually much easier and has fewer complexities, so get that working first.

And make a note after you get connected to install both inxi and lshw packages.  These make gathering information about the systems much easier.

---

### Post by awill10 on 2021-11-13
Thank you all for the replies, these were very helpful and cleared up the confusion I had about networking.

---

### Post by TheFu on 2021-11-13
Just to clarify.  Any network things that can be done on any other system, including nearly all enterprise routers, can be accomplished on Linux. Some will be easy. Some will be a little harder and some might require learning deep-networking internals of Linux to accomplish, but they are all possible.  

For example, I suggested never to enable wifi and wired connections at the same time.  This was because you said you were new.  It is common inside enterprises to have 6+ wired network connections on all their servers by default accessing 3+ internal networks. This is SOP at most enterprises where I've worked.  At smaller companies, I've seen and deployed systems with 1+ connection in all sorts of roles.  In my home lab, I have a system with 5 GigE ports connected. Most of the other servers have 3 NICs. I don't use wifi much at home. I treat all wifi like it is public internet connectivity and never trust it without a VPN.

---

