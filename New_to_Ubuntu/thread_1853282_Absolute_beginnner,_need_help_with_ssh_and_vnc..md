---
title: "Absolute beginnner, need help with ssh and vnc."
date: 2011-10-02
forum: New to Ubuntu
---

### Post by jrudi5of6 on 2011-10-02
Hi. i just started using Ubuntu to run a minecraft server with my friends. We had no experience with Ubuntu or command-line before this (so were pretty inexperienced), but the community's excellent support helped us.  We set up the port forwarding and the game server is working fine. The problem is that I Can't figure out how to set up ssh and vnc through the Internet; i can do it on my local network, but I can't manage it remotely. Ive read Ubuntu's guides, but as a newbie, it didn't make sense. Could anybody help me figure out how to do this or point me to a very basic step-by-step guide? Thank you in advance; we chose Ubuntu because of its great community support!

---

### Post by spiky001 on 2011-10-02
Hi you will have to forward your ssh port through the router, You would set this in the router configoration

---

### Post by papibe on 2011-10-02
Besides spiky001's tip, there are several things you need to do to make it work, and that implies understanding several concepts like static vs. dynamic IP addreses, DNS, etc. Then in your home network, static LAN IPs (or DHCP reservation), port forwarding, etc.

This is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.
Regards.

---

### Post by scorp123 on 2011-10-03
> **jrudi5of6 said:**
>  The problem is that I Can't figure out how to set up ssh and vnc through the Internet 

Why not use something else then? e.g. Teamviewer. It's free to use for private / non-commercial purposes. And it's dead easy to use. It's not more complicated than dialling a number on a phone. You don't need to know anything else, the application will handle the rest. Please read here:

[http://ubuntuforums.org/showpost.php?p=9750486&postcount=2](http://ubuntuforums.org/showpost.php?p=9750486&postcount=2)

As for having remote access whenever you need it: You can go into the "Options" menu and set a permanent password. So all you need to memorize is the ID of your desktop (e.g. 489 007 123) + permanent password ... baaaam ... you're connected.

And the performance is better than what you'd get out of SSH + VNC anyway. 

If you have an iPhone or Android phone: You can also download the Teamviewer free client for those phones and then easily remote control your desktop while being on the go ... 

That's as "easy remote access" as it could possibly ever get.

---

