---
title: "Ubuntu Server Remote RDP"
date: 2018-03-28
forum: New to Ubuntu
---

### Post by caballep on 2018-03-28
**Hello Masters!**

Since this is my first post and my second day playing with Linux i have 2 things to say before ask:
1. I am a noob at this.
2. I have the personal philosophy of two days that Linux is intimidating but not impossible to learn, at least the basics to take advantage as a developer.

[B]Here Starts my Question
[/B]
Alright, right now im paying a monthly 7 dlls vps from vpsdime provider, im using MovaXterm to connect to it by SSH protocol, the distro i picked is Ubuntu 16, no GUI.
So the first thing i did was install a GUI, i choose the ubuntu-desktop which i think its the deault one for ubuntu right?
Then i installed XRDP to take it remotly with Remote Desktop from my Windows work computer, but did not work... then i tried with the MovaXterm RDP Session and it seems to work, last message the Connection Log windows returns is "connection complete. connected ok" but the screen turns gray with strips and then it crashes and closes.

May this be caused by my provider?, like they are not allowing me to a)Install a GUI bymyself or B)Connect remotely by RDP protocol?, cause also they sell as Addon XRDP installation for 20 dollars when i can do it with one single command... do you guys think this is a restriction?, i am 100% sure i did installed it correctly.

This is what i get when i try to coonect:

[IMG]https://image.ibb.co/i970Zn/subir1.jpg[/IMG]

Then:
[IMG]https://image.ibb.co/cj59S7/subir2.jpg[/IMG]

---

### Post by TheFu on 2018-03-29
I wouldn't use RDP over the internet without a full, secure, VPN in place. That means either IPSec or OpenVPN for the VPN.  Anything less is asking to be hacked.   IMHO.

At least 1 side of the connection has to have an open port for the client to connect to the server. To connect to a work computer, then almost always means that the IT department at work would need to setup the remote port, which should be their own VPN, assuming they want to allow remote access at all.  
To connect to home, work has to allow outbound access AND your home IP needs to be known AND the router there needs to forward a port to the server you'd like to connect with.  It is also a smart idea to block all other IP connections from anywhere else in the world to that port.  Systems around the world are constantly probing my home public IPs - constantly.  When they find an opening, they determine the protocol and start trying to brute force it.  You'll definitely want more than default security.

There is ZERO need to pay for anything to get this working, if it can work at all.  It reads like you want to connect to a home computer from work, which seems backwards for how most people want to do this.  Please confirm.

If you can ssh from work to home, then you can use a tool called x2go, which uses the NX protocol. That includes using ssh for the tunnel of all traffic. ssh using ssh-keys is considered secure.  Using passwords is a security failure over the internet, regardless of protocol used. NX only needs ssh port open/working that the nromal openssh-server uses.  No other ports are needed.  x2go feels 2-3x faster than VNC.  RDP is Windows thing. Don't think there is an RDP server for Linux.  There is a solid x2go client for Windows, OSX, and Linux.  xrdp is a client rdp to connect to a Windows server.

I'm not certain I understand the networking involved based on the description. Sorry.
It would help if you were very clear about the client and the server - what is where, which software is on what.  I'm also extremely unclear about using an external VPN at all. Seems like extra hops and leaves your traffic in some data center that you or your company don't control.

---

