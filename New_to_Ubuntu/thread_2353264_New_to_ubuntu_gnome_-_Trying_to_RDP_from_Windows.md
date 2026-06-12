---
title: "New to ubuntu gnome - Trying to RDP from Windows"
date: 2017-02-20
forum: New to Ubuntu
---

### Post by rdabate on 2017-02-20
Hi, working on a new install of Ubuntu gnome, And a little new to Linux in general.  I'm not sure at this point what the best solution is. I found a post on XRDP, tired installing it, but it just hangs after attempting.  

So I'm wondering what the most stable solution is to RDP from a windows machine?

---

### Post by TheFu on 2017-02-20
Don't use RDP into Linux systems.  RDP is a MSFT protocol.

Prefer NX protocols on Linux, like x2go, over others. A case could be made to use some VNC method if you need android or iOS clients.  With VNC, be certain to use either an ssh-tunnel or a full VPN like openvpn. Never put VNC directly on the internet - NEVER.  When you setup the vncserver, be certain to use the --localhost option to prevent it from listening on non-local interfaces (thus enforcing secure tunnels).

There are many implementations of 'vncserver', but they all don't have the -localhost option, so either try to get that version or use the firewall to specifically block VNC connections from non-localhost sources.

x2go is easier, faster, and more secure.  There's a PPA for it. Load up the server on Linux and grab the Windows client installer + some fonts for Windows.  Very stable. Very fast.  Secure from anywhere in the world (well, as secure as any Windows machine is).

I've used x2go from 5 continents.

---

### Post by rdabate on 2017-02-21
I'm new to Ubuntu Gnome, and trying to figure out what to use so I can remote into it from Windows.  I came across XRDP from here,"[http://networkstatic.net/xrdp-an-easy-remote-desktop-setup-for-your-ubuntu-servers]("http://networkstatic.net/xrdp-an-easy-remote-desktop-setup-for-your-ubuntu-servers/")".  However, getting the error below.  Is anyone familiar with this app, or do you have another user friendly method?  

[ATTACH=CONFIG]273826[/ATTACH]

---

### Post by DuckHook on 2017-02-21
Please don't double post. It confuses those trying to help and dilutes community effort.

Threads merged.

---

