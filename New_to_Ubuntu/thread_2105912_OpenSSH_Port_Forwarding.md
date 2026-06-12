---
title: "OpenSSH Port Forwarding"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by dolphin194 on 2013-01-17
I have a computer at my house running Xubuntu 12.04 with an OpenSSH server, and I would like to forward all my traffic to that computer in order to access my files and folders securely over SSH. *I am currently connected to this server via VPN.*

My client is running Mac OS X 10.7, however the syntax for the OpenSSH client is exactly the same as Ubuntu.

What I have been doing is using [Proxifier]("http://www.proxifier.com/") to forward all my traffic through the socks proxy, however I would like to stop using that software because it is shareware.

_What I Have Done_
I know that if I forward dynamically with [FONT=Lucida Console]ssh -D1080 user@host[/FONT], I am able to set up my Firefox to use that dynamic forwarding port as a SOCKS proxy. I want to do this for an application that does not support a SOCKS proxy.

**I know this is possible** since you can tunnel a VNC connection through SSH, but I haven't figured out how to do that either.

---

### Post by papibe on 2013-01-17
Hi dolphin194.

I think what you need is a system wide proxy. Take a look at [this]("http://askubuntu.com/questions/15719/where-are-the-system-wide-proxy-server-settings").

Note that some applications, like Firefox itself, can be set to both follow the system settings or ignore them. In other words, it's up to the application to follow the proxy settings.

I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2013-01-17
Which application are you trying to forward and which port(s) does it use?

---

### Post by dolphin194 on 2013-01-17
> **papibe said:**
> 
Note that some applications can be set to both follow the system settings or ignore them. 
Regards.
The problem is the application I am trying to forward does not support a proxy.

> **Lars Noodén said:**
> Which application are you trying to forward and which port(s) does it use?
I am trying to forward FTP port 21.

---

### Post by papibe on 2013-01-17
FTP is an old and naughty protocol. It does not use exclusively port 21, as it open several other ports during its operation. I know it is not possible to tunnel it completely, and at this moment I don't know if it is possible configure it to use a proxy.

Alternative idea:

Since you are running a ssh server, it means sftp server it is already configured and ready to use. I would recommend taking a look at it.

Let us know how it goes.
Regards.

---

### Post by dolphin194 on 2013-01-18
That's the thing I need to route traffic that doesn't support a proxy through the proxy anyway.

Now, what if I was to try and forward a game like World of Warcraft? There are absolutely no options to configure the ports, and I need to use that Proxifier program to route the game through the proxy. 

Can I tunnel the ports used by World of Warcraft when it does not support a SOCKS proxy or do I have to use that Proxifier to forward all my traffic to the server?

---

### Post by papibe on 2013-01-18
What client are you using? 

Are you open to use another client? If so, I believe Filezilla is both available for Max OS X, and handle its own proxy settings.

Just a thought.
Regards.

---

