---
title: "likewise-open"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Garmuar on 2008-05-29
I have been trying to authenticate to adv.server2000 AD using Likewise.  When using the GUI or CLI domain join, I get:

Error code: CENTERROR_DOMAINJOIN_UNRESOLVED_DOMAIN_NAME (0x00080026)

Backtrace:
main.c:297
djmodule.c:158
djfirewall.c:685
djfirewall.c:609
djfirewall.c:297 

Others have looked at my Hosts file, nsswitch.conf, and resolv.conf, and said they were good.

Can anyone give me a clue as to whats happening by this error message above??

It just keeps saying that it can't authenticate DC name.  Everything pings using IP adress, the Ubuntu-desktop can not name translate on the LAN.  Internet NAT works fine.

---

### Post by vaporflux on 2008-05-29
I have the exact same problem as Garmuar.

---

### Post by mohenjo on 2008-05-29
Just curious, you said everything pings with IP addresses, but are you able to ping with just the name?  The error message stated unresolved domain, so to me it just sounds like there's a DNS issue there.  Check your DNS settings both on the workstation and server (particularly the event viewer on your 2k machine, as there may be some warnings or errors that may assist in pinpointing the exact cause).

---

### Post by vaporflux on 2008-05-30
I can only ping by IP, not by name. I can ping by name if I map my Win2003 server IP to its computer name in my hosts file on Ubuntu, but of course that's not quite the same. I entered the IP for my Win2003 computer as the DNS server for my Ubuntu computer but for some reason it's still not seeing it. I don't have any problems resolving names on the Internet. Also, I should probably mention that I don't have any issues connecting to the domain from any of my Windows computers, so DNS appears to be working for them - only Ubuntu is having an issue. I haven't checked the logs on Windows yet, I will have to do that. Sorry Garmuar, I hope it doesn't seem like I'm hijacking your post instead of starting my own; we're just having the exact same issue so it's nice to have the discussion in one place.

---

### Post by vaporflux on 2008-05-31
Garmuar - I can now successfully log onto to my domain, but the issue seemed to be with my Windows domain controller rather than with Ubuntu. I actually ended up re-installing Windows on my domain controller. Before the re-install, I had a single word domain name, so it was essentially "domainname" rather than "home.domainname.com" or something to that effect. I remember reading somewhere that that can cause issues (although my Windows computers never had a problem connecting). So, is your domain name by chance a single word?

---

### Post by Garmuar on 2008-06-03
yes it is one word.  Small Business Server 2000 lists it as 
domainname.local

Re-installing AD controllers in our working environment is not a practical solution though.  I am not quite sure how much of a pain it would be to rename our domain.  DNS is working fine in the windows network.

I just realized that our domain is running in Native Mode.  I hope that wouldn't have an effect on likewise.

---

### Post by JonRohan on 2008-06-06
I highly doubt that native mode would affect your connections to the server as you will still be using kerbros authentication.

---

### Post by Xerp on 2008-06-06
What domain name are you using when you join? The full domain string (like mydomain.co.uk) or the short version (like just "mydomain")? It certainly sounds like a faulty DNS.

---

### Post by Garmuar on 2008-06-09
I have tried both long and short domain name.  mydomain and mydomain.local.
neither work.

There are no errors or warnings in DNS logs and DNS is functioning fine for the rest of the the LAN/local domain.  I am running WINS server on the network though.  WINS maybe handling all of the local address translation.  Hardy Heron,likewise, can communicate with WINS right?

Just downloaded updates for Hardy and WINDBIND was one of them.  Maybe the update will effect some change.

---

### Post by Garmuar on 2008-06-24
I noticed that when I named the ubuntu machine, Ubuntu appended a -desktop to it for the host name.  I removed the "-desktop" changing the host name to a single word and it worked.  Now it is telling me I need to open some ports and I'll be in business.  

I know windows doesn't like special charectors in names. LOL  It seemed to fix the problem by removing the the dash.

---

### Post by vaporflux on 2008-06-24
Lame - it's annoying when a little thing like that causes so much trouble. I wonder what the deal is with the ports - I haven't touched the ports on my computer (Ubuntu closes most of them by default, right?) and I never had Likewise throw me any errors about ports. Or are you talking about ports on your domain controller?

---

