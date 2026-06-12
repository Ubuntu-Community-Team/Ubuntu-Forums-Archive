---
title: "How to make my Website online ?"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by darkflux9 on 2013-11-21
Hello currently running on ubuntu 12.04 . i have setup'ed everything and i dont know how to make to resolve the Dns . please help me step by stem . i am noob .

---

### Post by Lars Noodén on 2013-11-21
Where is your web site hosted and can you access it already via IP number?

---

### Post by darkflux9 on 2013-11-21
> **Lars Noodén said:**
> Where is your web site hosted and can you access it already via IP number?

[COLOR=#000000][FONT=Arial]5.254.101.70  ... yes it is ! my sellers said this

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]hello,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]in [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]/var/named-chroot/var/named/domain1.com[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]replace domain1.com with yours.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]There you add[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]YOUR DOMAIN IN A YOUR IP[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]--[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Best Regards,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Maximilian Kutzner[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ixam-Hosting.com // XDedicated.com


but they never saod how to do that via SSH . they know m noob but seems they are not helping .
[/FONT][/COLOR]

---

### Post by Lars Noodén on 2013-11-21
Ok.  Next step, which domain name do you have registered?  You have one, right?

If so, at which registrar?  The registrar will have a web interface you can log into and set your domain to point to your address  :  5.254.101.70

If not, you should either get one or else resign yourself to accessing the web site by IP number only.

---

### Post by darkflux9 on 2013-11-21
> **Lars Noodén said:**
> Ok.  Next step, which domain name do you have registered?  You have one, right?

If so, at which registrar?  The registrar will have a web interface you can log into and set your domain to point to your address  :  5.254.101.70

If not, you should either get one or else resign yourself to accessing the web site by IP number only.

yes its done . my website : pirateculture.org

next step please !

---

### Post by Lars Noodén on 2013-11-21
Which registrar?  Where are you renting the name from?  You have to log into their site and then set a host name, say [www.pirateculture.org](www.pirateculture.org), to point to the ip address you gave above.  Each registrar's interface is different, but most are fairly simple to use.

---

### Post by darkflux9 on 2013-11-21
> **Lars Noodén said:**
> Which registrar?  Where are you renting the name from?  You have to log into their site and then set a host name, say [www.pirateculture.org]("http://www.pirateculture.org"), to point to the ip address you gave above.  Each registrar's interface is different, but most are fairly simple to use.

its done mate the problem is my DNS is not resolving ( Nameservers )

Chrome note
.[COLOR=#444444][FONT=Helvetica]The webpage at [/FONT][/COLOR]**[http://www.pirateculture.org/](http://www.pirateculture.org/)**[COLOR=#444444][FONT=Helvetica] might be temporarily down or it may have moved permanently to a new web address.[/FONT][/COLOR][COLOR=#A0A0A0][FONT=Helvetica]Error code: ERR_NAME_RESOLUTION_FAILED[/FONT][/COLOR]

---

### Post by Lars Noodén on 2013-11-21
Right.  That error is expected.  You will get it until you put your IP number into DNS and associate it with a host name.  

Looking at whois, you may have registered with PrivacyProtect.  You need to log into their web site (not yours, yet) with the username and password you signed up to get the name and find their DNS management interface.

---

### Post by darkflux9 on 2013-11-21
> **Lars Noodén said:**
> Right.  That error is expected.  You will get it until you put your IP number into DNS and associate it with a host name.  

Looking at whois, you may have registered with PrivacyProtect.  You need to log into their web site (not yours, yet) with the username and password you signed up to get the name and find their DNS management interface.

Its what i got when i click DNS management .
[http://prntscr.com/25q6ra](http://prntscr.com/25q6ra)

Please what to do in that page :)

---

### Post by Lars Noodén on 2013-11-21
You would add one A record.  Use the name you want people to put into their browsers for the hostname and point it at the ip number you have.  From there, you should be able to find your way.  If you make many changes, it can take some time for them to propagate out to the public.

---

### Post by darkflux9 on 2013-11-21
> **Lars Noodén said:**
> You would add one A record.  Use the name you want people to put into their browsers for the hostname and point it at the ip number you have.  From there, you should be able to find your way.  If you make many changes, it can take some time for them to propagate out to the public.

ok ? [http://prntscr.com/25q95a](http://prntscr.com/25q95a)

---

### Post by Lars Noodén on 2013-11-21
Looks like it might OK.  You might want to add a CNAME ([www.pirateculture.org](www.pirateculture.org)) pointing to the A record (pirateculture.org)

The ultimate test will be when it works in your web browser.

---

### Post by darkflux9 on 2013-11-21
> **Lars Noodén said:**
> Looks like it might OK.  You might want to add a CNAME ([www.pirateculture.org]("http://www.pirateculture.org")) pointing to the A record (pirateculture.org)

The ultimate test will be when it works in your web browser.

[http://prntscr.com/25qdli](http://prntscr.com/25qdli)

please say what i need to put there :)

---

### Post by Lars Noodén on 2013-11-21
My guess would be that you would put "www" in the hostname box and then leave it at that.  

Read up a little on A records and CNAME records, so you get the idea of how they work.

---

### Post by darkflux9 on 2013-11-22
> **Lars Noodén said:**
> My guess would be that you would put "www" in the hostname box and then leave it at that.  

Read up a little on A records and CNAME records, so you get the idea of how they work.

thanks dude ! its worked !

---

