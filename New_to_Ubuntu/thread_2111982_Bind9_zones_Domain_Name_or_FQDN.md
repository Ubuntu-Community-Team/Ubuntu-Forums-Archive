---
title: "Bind9 zones: Domain Name or FQDN?"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by Roskow on 2013-02-03
Before coming to a forum to ask for help I really want to try my best to tackle something like this, but I am confused by Bind9. I follow these tutorials which seem to skip over details and make assumptions about the user's knowledge. I even watched a YouTube video where a guy begins entering a serial number and all the reply comments are asking where the hell that number came from.

It seems weird I even have to ask for clarification on this because it probably isn't that hard. Maybe my Google is weak but I'm not finding reference material to follow that gives me a working result.  

I have setup the forwarders in named.conf.options which is fairly straightforward. 


The question I have is on named.conf.local. Most tutorials have said to enter the Domain Name you want to use. However, I'm trying the Help.Ubuntu.Com guide now and noticed it says to replace "example.com" with my FQDN. This seems like a significant difference in directions, so I thought I should pin down whether a zone file uses Example.Com or [www.Example.Com](www.Example.Com).

*Simply replace example.com with your _FQDN_ (Fully Qualified Domain Name).*

[https://help.ubuntu.com/12.04/serverguide/dns-configuration.html](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html)

*Note:  Replace linux.rocks with the _internal domain name_ you picked *

[http://mixeduperic.com/ubuntu/seven-easy-steps-to-setting-up-an-interal-dns-server-on-ubuntu.html](http://mixeduperic.com/ubuntu/seven-easy-steps-to-setting-up-an-interal-dns-server-on-ubuntu.html)

---

### Post by sandyd on 2013-02-03
> **Roskow said:**
> Before coming to a forum to ask for help I really want to try my best to tackle something like this, but I am confused by Bind9. I follow these tutorials which seem to skip over details and make assumptions about the user's knowledge. I even watched a YouTube video where a guy begins entering a serial number and all the reply comments are asking where the hell that number came from.

It seems weird I even have to ask for clarification on this because it probably isn't that hard. Maybe my Google is weak but I'm not finding reference material to follow that gives me a working result.  

I have setup the forwarders in named.conf.options which is fairly straightforward. 


The question I have is on named.conf.local. Most tutorials have said to enter the Domain Name you want to use. However, I'm trying the Help.Ubuntu.Com guide now and noticed it says to replace "example.com" with my FQDN. This seems like a significant difference in directions, so I thought I should pin down whether a zone file uses Example.Com or [www.Example.Com](www.Example.Com).

*Simply replace example.com with your _FQDN_ (Fully Qualified Domain Name).*

[https://help.ubuntu.com/12.04/serverguide/dns-configuration.html](https://help.ubuntu.com/12.04/serverguide/dns-configuration.html)

*Note:  Replace linux.rocks with the _internal domain name_ you picked *

[http://mixeduperic.com/ubuntu/seven-easy-steps-to-setting-up-an-interal-dns-server-on-ubuntu.html](http://mixeduperic.com/ubuntu/seven-easy-steps-to-setting-up-an-interal-dns-server-on-ubuntu.html)
Its supposed to be example.com (FQDN)- [www.example.com](www.example.com) is a subdomain (the www at least).

---

### Post by TheFu on 2013-02-03
All that I can remember at this instance is don't forget the trailing {dot} unless you intend for the domain to be appeneded to it.

www
or
[www.example.com](www.example.com).

With the first line, the "example.com." will be assumed.

BTW, I was extremely frustrated with my first Bind install in the min-1990s. Couldn't find any complete set of instructions or examples. Ended up purchasing the O'Reilly book on DNS & Bind, read 6 pages, solved all my issues and it wasn't the trailing {dot} either. ;)

---

### Post by Roskow on 2013-02-03
okay maybe I'm getting turned around by use of terminology on different websites.  

The tutorial on MixedUpEric just refers to my chosen "internal domain name" at least when filling out the zone in named.conf.local with something like "example.com"

Than the tutorial says to create and edit a file like db.example.com then replace localhost. with my FQDN which I understand to be something like MyHost.Domain.Net.  


That's my understand from Eric's tutorial. It reads to me as if Host.Example.Com is a FQDN or the combined Hostname + DomainName. 

I might be so far off on this it's like I wandered into the woods and got lost. It kind of feels like it.

---

### Post by TheFu on 2013-02-03
Your systems can have multiple DNS Domain names.  There are internal only names that can be lots of fun.  

My internal TLD is .foo, as an example. I don't need to pay some registrar to use it.

My external DNS TLD is .com with a subdomain of jdpfu - that I had to purchase and re-new every decade.  I let a DNS provider handle the public IP addresses for me.

It can be complex to understand before you have a handle on everything.  The same Bind9 code that you run can run a TLD for the entire internet, so it understands many more complex things than you need. Those complex configurations are powerful AND hard to appreciate when you just want 2 domains - internal and external.  BTW, I was cracked through bind around 2002 because I was 3 months behind on a patch. Bind and sendmail are the most hacked services on UNIX, so if you run either on the internet, please do it inside a chroot environment and be certain you have great, automatic, versioned, backups.  Backups saved my bacon back then. BIG TIME!

sorry - after all that.
[www.example.com]("http://www.example.com").   = FQDN
example.com. = DN (Domain Name)

Obviously, Microsoft didn't help things when they decided to call the network peering "domains" - these have ZERO, nothing, nada to do with DNS.

---

### Post by Roskow on 2013-02-03
Well that's good to know.  

I came to this forum because I joined a college Cyber Defense team. Students try to learn about servers and security and build a network. We will be attacked by hackers and whatever team lasts the longest wins. (BTW someone on the team has to volunteer to run Mail on Debian)

The team accepts noobies so here I am picking my way through CLI.

---

### Post by SeijiSensei on 2013-02-03
Beyond the "domain name" example.com, there are two possible second-level entries.  The fully-qualified domain name of a host is hostname.example.com.  Usually that appears as an A or CNAME record in a zone file.  But you can also have subdomain.example.com.  In that case you would have an NS record for that entry in the zone file for example.com, and a separate zone file defined for subdomain.example.com.  

MX records always point to a domain name or a subdomain name; NS records point to the FQDN of a server that handles queries for that domain or subdomain.

Does that make sense?

---

### Post by Roskow on 2013-02-03
Clear as mud

Usually the second step in these tutorials covers the named.conf.local file.  Maybe I'm inaccurate in calling this a "Zone File" but this entry begins with the word zone so.......  

What follows in the underlined is why I started this thread.  At first I thought this entry could only be a domain like Example.Com.  The Help.Ubuntu.Com website suggests a FQDN goes in here, but if I'm understanding SeijiSensei correctly, the FQDN should be entered into another file like Db.Example.Com.  

zone **_"home.lan"_** {         type master;         file "/var/lib/bind/db.home.lan";         allow-update { key "rndc-key"; }; };
zone "5.168.192.in-addr.arpa" {         type master;         file "/var/lib/bind/db.5.168.192";         allow-update { key "rndc-key"; }; };


[IMG]http://cdn.memegenerator.net/instances/400x/31001720.jpg[/IMG]

---

### Post by Roskow on 2013-02-03
Another thought, would it be a good idea for a noobie to try putting in a GUI frontend for BIND?  

My OS is Ubuntu Server CLI, but I also have an Ubuntu Desktop netbook that can talk  to my server on the LAN.  

Would anyone have a GUI recommendation?  In the long run I do want to tackle most things from CLI. I'm thinking if this method helps me successfully configure DNS naming then I can later go in the terminal to look at the files and see what I was doing wrong.

---

### Post by TheFu on 2013-02-03
"home.lan" is the FQDN in the example. It is for an internal network only.  The TLD would be ".lan." - similar to ".net." or ".com." on the regular internet.

---

### Post by TheFu on 2013-02-03
> **Roskow said:**
> Another thought, would it be a good idea for a noobie to try putting in a GUI frontend for BIND? 

Sure - go for it.
I'll be manually editing zone files with vi myself, but you will definitely learn a bunch in your efforts to simplify this.

There are webtools that will create zone files with forward and reverse lookups on the internet.  I have used them before. Google will find those.

---

### Post by Roskow on 2013-02-03
Okay another tutorial identified the HostName.Example.Com as the FQDN and led me astray  into terminology confusion.

---

### Post by Roskow on 2013-02-03
Going through this again by following the Help.Ubuntu.Com guide.  

Right now in the Db.192 file.  For the SOA or first PTR the template shows it as ns.example.com.  

I'm not sure if the assumption is I change "ns" to my hostname?  Or do I leave that as NS.Domain.Com?

I'm hoping this is the last detail I need to iron out and maybe I can get this working.

---

### Post by Roskow on 2013-02-03
OMG I may have it.  

Did a host [IPaddress] look up and it came back with my assigned domain name.  

Successfully PINGed a new domain name on my LAN.  

I cannot believe how incomplete tutorials are for Bind9.  Yes we are noobies and should be told details like adding the new DNS nameserver to /etc/network/interfaces.  Otherwise you'll think you can test it and you'll fail.

I'm going to have to reverse engineer the process and make my own cheat sheet I can follow.

---

### Post by SeijiSensei on 2013-02-03
Some of the tutorials for distributions that are more commonly used on servers like RedHat are more extensive, but the organization of the configuration and zone files is quite different from that used in Debian and Ubuntu.  So, like TheFu, I taught myself DNS configuration from the excellent O'Reilly books.  I have a copy of *DNS & BIND*, but the single most useful book I read was Craig Hunt's [TCP/IP Network Administration]("http://www.amazon.com/TCP-Network-Administration-OReilly-Networking/dp/0596002971").  It covers many more subjects than just DNS, and Hunt writes clearly throughout.

---

### Post by Roskow on 2013-02-03
I seem to be able to ping this domain or even type Host 192.168.254.70 and have it return my domain name. But only on my server. Anything other computer on my LAN can't seem to find it.

---

### Post by Roskow on 2013-02-04
Well finally it works. Getting browser, nslookup, and pings with other computers on the LAN.  

I'm going to admit that somehow when I moved back in a VM Snapshot the Firewall came back on. I'm sharing that as a warning to other noobies. When in doubt check UFW Status. ermahgerd.


edit:  I'm not sure if I can switch to SOLVED or if I need more beans. If a Mod sees this feel free to do so.  

Also, while I was meandering all of the place you guys did help me clear up some terminology. I think a tutorial I followed had me confused.

---

### Post by Roskow on 2013-02-04
Ironing out details. Put DNS-nameserver and search domain into /etc/resolv.conf on my Ubuntu Desktop netbook and it hooked on. 

Also put it into a Windows machine under IPv4 Properties, Advanced, and added DNS suffix.

---

### Post by TheFu on 2013-02-04
> **Roskow said:**
> Ironing out details. Put DNS-nameserver and search domain into /etc/resolv.conf on my Ubuntu Desktop netbook and it hooked on. 

Also put it into a Windows machine under IPv4 Properties, Advanced, and added DNS suffix.

In 12.04 and later, modifying the /etc/resolve.conf is considered poor form and it is likely to be overwritten the next time networking is restarted.  You really need to use the /etc/network/interfaces settings for DNS, if your DHCP server does not provide them.  I would find the configuration issue inside the DHCP server and fix it 1 place if I had the same problem you are having.

* "ns" is a common name for nameservers.

* Machine hostnames and DNS names do not need to match.

* Every machine can have hundreds (thousands, millions?) of names, dns entries, aliases, whatever you want to call them.

Do you really think that all those [www.domain.com](www.domain.com) computers are actually named "www"?  NO WAY!  that is just a DNS thing and it really means absolutely NOTHING.  ftp.domain.com, smtp.domain.com, zyx.domain.com mean nothing.  They are just setup as a memory trick and by convention, nothing says those names must be used.  Even TLD (Top Level Domains) are by convention only.  There are very few restrictions on what the actual names can be - you can find those restrictions in the RFC.  The short version is 
* no underscores (dashes are fine)
* must start with an alpha or numeric character
* cannot be longer than ZZ - I can't recall the exact limitations, but 64 characters comes to my mind.
* It used to be mandated that 7-bit ASCII characters be used, but I think that was changed a few years ago - much of the world does not use only ASCII alphabets, so it makes sense for them to have native characters in the domainnames and URLs. This also opens old code to abuse, since many characters that look like the 7-bit ASCII exist in those other alphabets, but computers do not see them as the same. That means domain spoofing is much easier.

Be certain that both forward and reverse lookups work as you expect.

---

### Post by Roskow on 2013-02-04
Thanks for the trouble shooting tips.  I had some idea that the resolv.conf might be over written on my Ubuntu netbook. I was not sure about the Debian machine running VirtualBox but after reboot it seems that one was knocked out to.

---

