---
title: "LAN fileserver/webpage testing server behind a NAT. Security concerns?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-07-16
I’m just starting out with Linux and am wondering how much attention I should pay to security issues and configurations. Years of experience with a WinBox has me conditioned to be paranoid about security, so taking it lightly gives me the screaming heebie-jeebies. But the inherent security of Linux (which I understand doesn’t mean perfect security, and that configurations I make could open giant holes) and the use to which I’m putting it makes me think I can be fairly relaxed. 

The box I’m putting together will be cable-connected to the LAN, with a Linksys WRT54G router’s NAT between it and the Internet. I have no ports forwarded on the router, and those rare occasions when I do need to open something up I close/remove the configuration as soon as the need is over. So, unless I’m grossly mistaken about the NAT’s function no one outside the LAN will ever see the Linux box. 

Or could they? Can a less-than-obvious configuration open and broadcast a port to the wider world? Can a virus that infects one of the machines in the home office (Windows and Mac) find its way to the Linux box? I’ll have it mapped as a network drive on both machines with full privileges to a folder off /home. I’d think that while a Windows virus could delete files, it couldn’t do much to the general state of the Linux machine. Also, I have the permissions set only for that folder, not anywhere else. 

The only two things I’ll be using the Linux machine for is serving files between the office computers, and using it as a PHP/MySQL testing server before uploading them to our/clients’ sites. My wife and I are the only ones who work here, so all connected machines/users are trusted. 

So, for example, at the moment I’m trying to figure out how to configure Gproftpd/ProFTPD to allow Dreamweaver to send it files (trying being the operative word). A lot of pages talk about security settings, but since they are primarily discussing setting it up as a public FTP, they necessarily delve into security settings and issues. How much attention do I need to pay to such concerns? Am I being naive in thinking *not much*?

Oh, if I ever want to do more with the box I will revisit security issues. 

Thanks, 

Rhythm

---

### Post by baeksu on 2008-07-16
> **Rhythmdvl said:**
> The box I’m putting together will be cable-connected to the LAN, with a Linksys WRT54G router’s NAT between it and the Internet. I have no ports forwarded on the router, and those rare occasions when I do need to open something up I close/remove the configuration as soon as the need is over. So, unless I’m grossly mistaken about the NAT’s function no one outside the LAN will ever see the Linux box. 

Assuming the NAT is functioning as it should (and they usually do), no one can get in, except if they manage to infect and own another machine in your LAN, or if there is a WLAN connection they can use.


> **Rhythmdvl said:**
> Or could they? Can a less-than-obvious configuration open and broadcast a port to the wider world?


Well, there is [UPNP](http://en.wikipedia.org/wiki/Upnp), but you should turn that off at the router level anyway.

> **Rhythmdvl said:**
>  Can a virus that infects one of the machines in the home office (Windows and Mac) find its way to the Linux box?

Though the virus in itself won't be able to run on the Linux box, if someone owns your Windows or Mac boxes, they will have the same access to the server as you would, including all the passwords you have used or will use.

> **Rhythmdvl said:**
> A lot of pages talk about security settings, but since they are primarily discussing setting it up as a public FTP, they necessarily delve into security settings and issues.

The problem with FTP is that it is not encrypted. Though this is not a problem within your LAN, it would be a problem if you use FTP over a public network, as then your user id, password, and all the data will be visible to anyone who has access to any of the machine your traffic passes through.

---

### Post by bodhi.zazen on 2008-07-16
In general you should be fine. You can configure http to allow access from localhost only and your are behind a router.

You might like this link : [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by Rhythmdvl on 2008-07-17
Thanks heaps for the reassurance. Router is tied up as tight as I can make it (no UPNP) and no one else is in the network. I'll still keep an eye on what security information relevant to something I'm doing, but I won't sweat it. Yet. Until I convert my Winbox over. (But I think that's a bit off.)

---

### Post by Rhythmdvl on 2008-07-17
Ok, I'm happily setting up PHPMyAdmin now (finally got FTP and whatnot to work, so Dreamweaver is connecting fine). 

On a scale of *Sack of Hammers* to *Inventing Post-It Notes*, how dumb would it to be to keep the same, basic, simple, easily hackable but oh-so-rememberable password for all functions? I can see maybe keeping root password different so as to not emasculate the purpose behind sudo, but what about everything else? Again, there are no internal security concerns to worry about (well, one of the pooches tends to misbehave, but his paws are too big to use a keyboard effectively)?

---

