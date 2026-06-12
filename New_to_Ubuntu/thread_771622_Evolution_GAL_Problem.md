---
title: "Evolution GAL Problem"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by indicava on 2008-04-27
Hi All,

(Posted here caused I couldn't find a proper category).

I am using Evolution 2.22.1 from final Hardy release. I am using Evolution to connect to my company's exchange server (over an internet connection). Everything seems to be working fine (stability is not at its best).

The one issue is with contacts, I can't search for them and they don't auto-complete when typing in names on a new message's "to" field. Generally speaking, I have found no way to see my company's contacts.

I played around a lot with the Global Address List server name field trying a lot of options I found in posts on the net. None of them worked (BTW: leaving it empty spiked my CPU hard, but I read somewhere thats already reported as bug).

Does Evolution rely only on the GAL server for contacts, can't it grab them from the OWA? If the GAL is my company's DC then there is no way I can connect to it over the internet (and I doubt there is any company which opens its DC to the net).

Any suggestions?

P.s. 
Hardy rocks! The best dist I ever installed. I am 4 days (since Hady was released) into my "month-of-linux" which means I am trying not to have to reboot into Vista for one month. If that succeeds, I will start planning a full migration. I work as an IT consultant and I use my lap 14-15 hours a day, about ~20% of that time is using Outlook so Evolution's functionality is a big criteria for me.


Thanks,
Indicava

---

### Post by tact on 2008-09-09
I realise this reply comes many months after the OP posted.  But recently I was looking for the same kind of help (thats how I found this thread) and found that there is not a lot of good experienced help for this bit of functionality.

I think I have managed to get GAL lookups and access to corporate global address lists working as well as it can with the present level of development with Evolution.   So since I have some info to share I thought I better share it.

The OP is correct in that the GAL server in many organisations is the Active Directory server (or one of them).  You need to know which server name or address to use in the setup for a start and ...  again the OP is correct...  if you are not ON the corporate LAN (directly or via VPN etc) then you will not have access to the domain controller or AD servers etc.

For me I can get GAL lookups working when conencted to the company LAN directly, or when remote but connected via VPN

So the challenges so far are:
-  knowing what is the AD or DC server name for proper configuration
-  having access to corporate LAN (without it you have no access to windows services such as global addressbook)

Now the limitations...
-  When you are set up and connected properly you cannot get a full listing of the corporate global addresslist to browse.  This is documented and the reason being to "reduce load on servers/network" or some such thing.
-  What happens is that you type in part of a name in the search box and only then those entries matching the search term are fetched for you to choose from.
-  autocompletion from local or global address books works when composing email  You do need to select which addressbooks to use for autocompletion in the Evolution preferences.
-  Scheduling meetings, finding the free/busy times for people on the global addressbook, also works fine so long as you have selected the global calendar

---

### Post by once111 on 2008-09-11
I was just researching this Global Address List lookup issue myself, and after playing with it for a while, I found that adding the Global Catalog, which houses the Global Address List, port number to the server name helped me.  For example, GC on a DC is port 3268 by default, so I added this:

*servername.domain.com:**3268***

After that and telling Evolution which address lists to use for auto completion, it's been working like a champ.

---

### Post by melbo on 2008-12-30
the part I don't understand about Evolutions complex way of getting to the GAL or Company Directory is that when I am handed a new Smartphone, all I have to do is type in the companies webmail server address, my username and password and I can look up and access all of my company contacts.  This is on a phone and works under a number of different carriers and does not use my VPN.  I know it's not hooked to the VPN because I can't access my company Intranet on the phones browser.

Seems like it should be really simple to get this to work and maybe Evolution has went after a complicated route that requires ports and pots and etc.

I'd love to get this working myself but my IT dept is NOT going to give me my server info to run on non-compliant OS'

---

### Post by Aykhalifa on 2009-04-05
Hi all,
I have a evolution ver 2.24.3 and had troubles finding out how to configure the gal inside company network on exchange 2003 , finally I successfully got it working , I was trying to put the FQDN and wasn't working until i just put the domain without the email server name in front of the address . finally:)

---

### Post by archenroot on 2011-01-19
Hi,

I just wait until all the required port 3268 for GAL will be opened on the firewall and then play with functionality of connecting to Exchange with evolution using the connector, not the IMAP.

Aykhalifa,
so if my FQDN is dc1.domain.mynet.com. domain is the name of the domain controlled by domain controler dc1, you think that I schould use DOMAIN\dc1 syntax?

Thanks.

Ladislav

---

### Post by archenroot on 2011-01-19
Hi,

I just wait until all the required port 3268 for GAL will be opened on the firewall and then play with functionality of connecting to Exchange with evolution using the connector, not the IMAP.

Aykhalifa,
so if my FQDN is dc1.domain.mynet.com. domain is the name of the domain controlled by domain controler dc1, you think that I schould use DOMAIN\dc1 syntax?

Thanks.

Ladislav

---

