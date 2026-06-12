---
title: "Enabling ubuntu desktop sharing from ssh"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by roman25 on 2017-06-23
So I have ssh connection to Ubuntu 16.04 PC, and I want to enable desktop sharing on that PC to VNC login and make some graphical stuff. As I searched on this forum I must type
```
DISPLAY=:0 gsettings set org.gnome.Vino enabled true

DISPLAY=:0 gsettings set org.gnome.Vino require-encryption false
```
[COLOR=#000000][FONT=&quot]
But when I type it in putty . I get 
[/FONT][/COLOR]```
Usage:  gsettings [--schemadir SCHEMADIR] set SCHEMA[:PATH] KEY VALUE


Set the value of KEY to VALUE


Arguments:
  SCHEMADIR A directory to search for additional schemas
  SCHEMA    The name of the schema
  PATH      The path, for relocatable schemas
  KEY       The key within the schema
  VALUE     The value to set



```

So something in my commands is wrong. What is the correct command?

---

### Post by TheFu on 2017-06-23
I don't know **anything** about gsettings or vino.

ssh tunneling isn't hard and commonly used to tunnel vnc-server connections.
[https://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](https://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html) explains. That is a reputable how-to site, IMHO.

---

### Post by roman25 on 2017-06-24
Ok what if I want to login from windows? How can I do it from putty?

---

### Post by TheFu on 2017-06-24
I use x2go from Windows for a remote desktop. It is 2-3x faster than vnc/rdp and uses only ssh for all network traffic. I've used it from 2 ft away or 10K Km away.

But that doesn't help you.  I haven't used putty for anything complex in over a decade, sorry. Bet there are lots of how-tos for VNC using putty.

---

### Post by roman25 on 2017-06-24
thanks for directions. I'll try them out

---

### Post by TheFu on 2017-06-24
> **roman25 said:**
> thanks for directions. I'll try them out

We assume you used google before posting here.  If I find 50 how-tos with no real effort, well, chances are that you can find 10.  The only warning is to **Never** copy/paste from any HTML source and try to stay with reputable websites for instructions.  Always start with those sites that have "ubuntu" in their names.  help.ubuntu.com is the tops.  Then you can drop down into these forums, askUbuntu and OMGubuntu places.  The next tier is VPS hosting how-tos - those folks have a desire for their customers to bring up services, safely, in a secure manner, with the shortest number of steps.

I hope you mean to try out x2go. It is an amazing tool.  Just follow the instructions and use the PPA from the x2go project site.  On Windows, the only trick is to install all the font packages. The normal x2go client for Windows includes all the other stuff you need.  x2go-servers only run on Linux systems, so you cannot directly connect to a remote Windows machine using it, but since Windows RDP/VNC is inherently non-secure, you don't want to do that anyway.

Hope you've noticed that security is always a consideration. ALWAYS.  Even on the same LAN, I avoid using non-secure protocols.

---

### Post by HermanAB on 2017-06-25
Why don't you start with the simple case using ssh only?

If your desktop is running an X server (if Windows, you need Cygwin), then simply do something like this:
$ ssh -X -C -c blowfish user@ipaddress nautilus

The thing to bear in mind is that you don't really need to remote the whole desktop since your local machine already has one.  It is more efficient to only remote the program that you want to run and let it pop up transparently on the local desktop.

---

### Post by TheFu on 2017-06-25
HermanAB is correct, when on the same LAN, if you have a local X/server.  However, Windows doesn't generally come with an X/Server and the free versions have never impressed me.  The commercial X/Servers for Windows where $140 last time I checked and usually beyond the ability of newbies to get working.

Over the WAN, with much less bandwidth, X/Windows doesn't perform well at all. X/Windows gets extremely slow over the WAN, unless you have GigE WAN connections for all connections. Typical 25/5 connections are very painful to use, IME.

x2go works surprisingly well in both situations.  It can be used to watch video on the LAN, don't expect the result to be great, but it does work. Productivity apps sing over the LAN. Over the WAN, if you tweak the bandwidth and image compression, it works acceptably. I test with spreadsheets and remote PgDn/PgUp refreshes.

---

### Post by steeldriver on 2017-06-25
FWIW I don't see anything wrong with your gsettings commands, as typed - you might also try

```

DISPLAY=:0 gsettings list-recursively org.gnome.Vino

```

to see what the current settings are.

Once you get the server side working, the client side just involves adding a suitable tunnel to your putty session:

[ATTACH=CONFIG]275764[/ATTACH]

then pointing your VNC client at localhost:5900

HOWEVER you may find that the Unity/Ubuntu desktop doesn't work well (if at all) over VNC

---

