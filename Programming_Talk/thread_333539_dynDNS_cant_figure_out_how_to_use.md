---
title: "dynDNS cant figure out how to use"
date: 2007-01-07
forum: Programming Talk
---

### Post by theorem_hunter on 2007-01-07
i hav a account with dynDNS, i have read most of the support pages on there site but cant figure how to host a web page. i just want to test it.

so far, i can update my IP in their data base.
i can ping my IP & the host name i chose :)
but when i type the IP or host name into firefox it asks me for a username & passwork...
so i type the username & password for my dynDNS account, which fais...

so im stuck. :-k 

ultimately i want to ssh into my home pc from work.

thanks

---

### Post by stucky on 2007-01-07
So you are able to log into your account on DynDNS? 

Are you behind a firewall or running through a router that supports DDNS?

---

### Post by maxamillion on 2007-01-07
[http://www.no-ip.com/](http://www.no-ip.com/)

that's the dynamic dns service i use and they even have a client for updating your ip at your designated intervals that is available in the repositories

[http://packages.ubuntu.com/edgy/net/no-ip](http://packages.ubuntu.com/edgy/net/no-ip)

---

### Post by Xriva on 2009-09-04
Ye That Know,

I plan to support a remote computer using a VNC product.

I need a static IP to do this.  Since I don't have a static IP, I set up an account with DynDNS and installed the "update client" on my local computer.

Here's the question:

How do I use it ?   **For example, if the VNC software requires an IP in its' setup folder, what do I put in there ?  In place the the IP, should I enter the custom host domain name DynDNS created for me ?**

It seems odd to me that this detail isn't mentioned anywhere.

-:> Xriva

PS:> Attached is the VNC config file, if that's helpful.

---

### Post by dwhitney67 on 2009-09-04
> **Xriva said:**
> ...
**For example, if the VNC software requires an IP in its' setup folder, what do I put in there ?  In place the the IP, should I enter the custom host domain name DynDNS created for me ?**

Yes.

> **Xriva said:**
> 
It seems odd to me that this detail isn't mentioned anywhere.

Does it have to be?  One would presume that you are aware that a URL is auto-magically translated to an IP address using one or more DNSs.  Read [here]("http://en.wikipedia.org/wiki/Domain_Name_System") for enlightenment.

P.S.  I am not familiar at all with VNC, but I do SSH from work to my home computer on occasion.  I use my DynDNS assigned URL when specifying the address to SSH.

---

### Post by Hanratty on 2009-09-04
[LIST]
[*][Step One: Test Your Server]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#checkserver")
[*][Step Two: Test Your IP Address]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#testip")
[*][Step Three: Test the Port]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#testport")
[LIST]
[*][Check your firewalls and router]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#testport-firewall")
[*][Try an alternate port]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#testport-altport")
[/LIST]
 
[*][Step Four: Check the DNS]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#checkdns")
[LIST]
[*][Check the database]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#checkdns-db")
[*][Check the host in DNS]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#checkdns-dns")
[/LIST]
 
[*][Common Problems]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#common")
[LIST]
[*][Other people can reach my server, but I can't view it locally.]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#common-loopback1")
[*][If I visit my host, it brings up my router.]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#common-loopback2")
[*][I can ping my host, but I can't view my server.]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html#common-ping")
[/LIST]
             
[/LIST]

---

### Post by falconindy on 2009-09-04
DynDNS doesn't do hosting of any sort. They merely provide a name that redirects to an IP address. If you wanted to host a webpage at the destination that this name points to (and it sounds like it points to your router), you'd have to be running apache somewhere on your network and have your router port forward to that computer. Similarly, if your goal is to be able to SSH to your computer using this name, you'll need to open port 22 to your computer.

You haven't provided us with a whole lot of info, but I'm guessing that the username and password you're getting prompted for is being requested by your router's web interface.

---

### Post by Xriva on 2009-09-04
Thanks to everyone who responded . . . even those who implied I'm ignorant.  I suppose it's a relative matter of opinion.

IMHO, DynDNS and numerous HOW-To documents discuss configuring a VNC and using DynDNS to "handle" the dynamic IP problem.  They give tons of step by step detail.  Then to not give THIS detail. That still seems a little odd to me . . .  just my two cents.  You're welcome to disagree.

In any case, I am thankful for the replies as I now know what to do and will test it tonight.

-Xriva

----------
***_Old_***
[HOST]
Dubble Click >HERE< to make a connection
-connect 192.168.1.102:5500 -noregistry

***_New - using DynDNS_***
[HOST]
Dubble Click >HERE< to make a connection
-connect mycustomehostname.dyndns.info:5500 -noregistry

---

