---
title: "Newbie lost in the BIND9 forest"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by Lico on 2012-06-30
Hello Ubuntuers!!
I'm a complete newbie and I'm trying to get my BIND9 configuration correct on a VPS. I've already followed four guides and none of them lead me to a result different from SERVFAIL :( . I'm asking for help as a last resort because I've spent the last days visiting all solved threads i could find on the web and none helped me. If anyone could point me out what I'm doing wrong (I'm pretty sure it's a lot of things) I'd eternally grateful.

some info:
Running ubuntu 11.04

Domain: tincgaming.com

IP i'm trying to get [www.tincgaming.com](www.tincgaming.com) to point to (the VPS IP): 200.160.239.84

firewall: UFW, with bind9 allowed

some configuration files:

[COLOR="Red"]/etc/bind/zones/tincgaming.com.db[/COLOR]
```

; BIND data file for tincgaming.com
 ;
 $TTL 14400
 @ IN SOA ns1.tincgaming.com. indo.tincgaming.com. (
 2012063003 ; Serial
 7200 ; Refresh
 120 ; Retry
 2419200 ; Expire
 604800) ; Default TTL
 ;
 tincgaming.com. IN NS ns1.tincgaming.com.
 tincgaming.com. IN NS ns2.tincgaming.com.

tincgaming.com. IN MX 10 mail.tincgaming.com.
 tincgaming.com. IN A 200.160.239.84

ns1 IN A 200.160.239.84
 ns2 IN A 200.160.239.84
 www IN A 200.160.239.84
 mail IN A 200.160.239.84
 ftp IN A 200.160.239.84
 cachecluster.com. IN TXT "v=spf1 ip4:200.160.239.84 a mx ~all"
 mail IN TXT "v=spf1 a -all"
 @ IN A 200.160.239.84
localhost IN A 127.0.0.1

```

[COLOR="red"]/etc/bind/named.conf[/COLOR]
[COLOR="red"]AND[/COLOR]
[COLOR="red"]/etc/bind/named.conf.local[/COLOR]
```

//
// Do any local configuration here
//

# This is the zone definition. replace example.com with your domain name

zone "tincgaming.com" {
 type master;
 file "/etc/bind/zones/tincgaming.com.db";
 };

# This is the zone definition for reverse DNS. replace 0.168.192 with your netw$

zone "84.239.160.200.in-addr.arpa" {
 type master;
 file "/etc/bind/zones/rev.84.239.160.200.in-addr.arpa";
 };

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```

[COLOR="red"]/etc/bind/zones/rev.84.239.160.200.in-addr.arpa[/COLOR]

```

@ IN SOA tincgaming.com. indo.tincgaming.com. (
 2012063003;
 28800;
 604800;
 604800;
 86400 );

IN NS ns1.tincgaming.com.
 4 IN PTR tincgaming.com.

```

[COLOR="red"]/etc/hosts[/COLOR]
```

]::1            localhost ip6-localhost ip6-loopback
fe00::0         ip6-localnet
ff00::0         ip6-mcastprefix
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters

127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
200.160.239.84 tincgaming
127.0.0.1       ns1     localhost.localdomain   localhost       www     mail   $
200.160.239.84 tincgaming.com

```

I've also tried to obtain error logs but it seems like bind9 starts without a problem, even though it doesn't work D: D; D:

The error (obtained by using dig)
```
 dig tincgaming.com

; <<>> DiG 9.7.3 <<>> tincgaming.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 35601
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;tincgaming.com.                        IN      A

;; Query time: 488 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Jul  1 03:06:35 2012
;; MSG SIZE  rcvd: 32

```

In the website I registered the domain, i have the option to add NAMESERVERS, where i can add (BLANKSPACE).tincgaming.com and set an IP. Is this related to my configuration? also, they have two unneditable nameservers named as 
"ns3.servidorwebsite.net"
and
"ns4.servidorwebsite.net".
What does these mean? i should use them insted of google's DNS (8.8.8.8 and 8.8.4.4 from what I get) or they should be somewhere else in my configuration?

(Note: when I connect via IP, I do see the test page i put up thought apache2, so i think the problem really is the DNS config).

Please guys, HELP!!!

Thanks in advance!!!

---

### Post by cryptotheslow on 2012-06-30
Firstly you can check your zone files are loading correctly with these commands:

```

named-checkzone tincgaming.com /etc/bind/zones/tincgaming.com.db

named-checkzone tincgaming.com /etc/bind/zones/rev.84.239.160.200.in-addr.arpa

```

Both should respond with OK results like:

zone tincgaming.com/IN: loaded serial 10000
OK

The serial numbers in the messages should match those in your zone files.

On your domain registrar I'd think you enter the extra nameserver as ns1.tincgaming.com. Is there anywhere in the domain control panel you can see what records they have configured on ns3 and ns4.servidorwebsite.net ?

---

### Post by Lico on 2012-06-30
> **cryptotheslow said:**
> Firstly you can check your zone files are loading correctly with these commands:

```

named-checkzone tincgaming.com /etc/bind/zones/tincgaming.com.db

named-checkzone tincgaming.com /etc/bind/zones/rev.84.239.160.200.in-addr.arpa

```

Both should respond with OK results like:

zone tincgaming.com/IN: loaded serial 10000
OK

The serial numbers in the messages should match those in your zone files.

On your domain registrar I'd think you enter the extra nameserver as ns1.tincgaming.com. Is there anywhere in the domain control panel you can see what records they have configured on ns3 and ns4.servidorwebsite.net ?

Hello Cryptotheslow
thank you for awnsering me!!
I've tried the commands you suggested and got error messages D:

```
 named-checkzone tincgaming.com /etc/bind/zones/tincgaming.com.db
/etc/bind/zones/tincgaming.com.db:3: no current owner name
/etc/bind/zones/tincgaming.com.db:4: no current owner name
/etc/bind/zones/tincgaming.com.db:11: no current owner name
/etc/bind/zones/tincgaming.com.db:12: no current owner name
/etc/bind/zones/tincgaming.com.db:14: no TTL specified; zone rejected
/etc/bind/zones/tincgaming.com.db:15: unknown RR type 'tincgaming.com.'
/etc/bind/zones/tincgaming.com.db:17: no TTL specified; zone rejected
/etc/bind/zones/tincgaming.com.db:18: unknown RR type 'ns2'
/etc/bind/zones/tincgaming.com.db:19: unknown RR type 'www'
/etc/bind/zones/tincgaming.com.db:20: unknown RR type 'mail'
/etc/bind/zones/tincgaming.com.db:21: unknown RR type 'ftp'
/etc/bind/zones/tincgaming.com.db:22: unknown RR type 'cachecluster.com.'
/etc/bind/zones/tincgaming.com.db:23: unknown RR type 'mail'
/etc/bind/zones/tincgaming.com.db:24: unknown RR type '@'
/etc/bind/zones/tincgaming.com.db:25: no TTL specified; zone rejected
zone tincgaming.com/IN: loading from master file /etc/bind/zones/tincgaming.com.db failed: no owner
zone tincgaming.com/IN: not loaded due to errors.

```

and

```
 named-checkzone tincgaming.com /etc/bind/zones/rev.84.239.160.200.in-addr.arpa
/etc/bind/zones/rev.84.239.160.200.in-addr.arpa:1: no TTL specified; using SOA MINTTL instead
zone tincgaming.com/IN: has no NS records
zone tincgaming.com/IN: not loaded due to errors.

```

I have absolutely no idea what this means!!! What should I do:confused::confused:??

I've added ns1.tincgaming.com to the nameserver list, but i can't find the records they've setted in ns3 and ns4.servidorwebsite.net .

Thanks again, i know it takes a lot of patience to handle noobs like me.

---

### Post by cryptotheslow on 2012-06-30
Out of interest - do you need to run your own BIND server? Couldn't you just add the required A / MX records etc. to the servidorwebsite.net DNS configuration?

At the moment ns3 and ns4.servidorwebsite.net DNS servers aren't returning any records for your domain which is why you are seeing that SERVFAIL message. That has nothing to do with your BIND configuration as your new nameserver is not listed as such on your domain.

---

### Post by Lico on 2012-06-30
> **cryptotheslow said:**
> Out of interest - do you need to run your own BIND server? Couldn't you just add the required A / MX records etc. to the servidorwebsite.net DNS configuration?

At the moment ns3 and ns4.servidorwebsite.net DNS servers aren't returning any records for your domain which is why you are seeing that SERVFAIL message. That has nothing to do with your BIND configuration as your new nameserver is not listed as such on your domain.

I asked them to do my reverse DNS configuration and they replied saying that since i subscribed to a "pure" VPS (I didn't want any kind of assistance or adminPanel because not only their license is expensive but i've also heard that they have lots of security flaws) i'd have to configure myself, through my own dns server...

EDIT: my VPS is being hosted by [https://www.tifacil.com.br/](https://www.tifacil.com.br/) , not servidorwebsite.net , i'm not sure if this info is relevant, altought it seems like they are associated sites.

---

### Post by cryptotheslow on 2012-06-30
OK so you registered your domain with servidorwebsite.net separately to where you got the VPS from?

Or did you register the domain at the same time as getting the VPS and they are both from the same company?

---

### Post by Lico on 2012-06-30
I got both the VPS and the domain from tifacil.com.br, I hav eno idea why those ns3 and ns4.servidorwebsite.net were in my nameserver list... i tought i had to right to use them or something :S

---

### Post by cryptotheslow on 2012-06-30
Well in setting up your domain they have listed those two servers as authoritative for your domain - so even if you get your own BIND config up and running and added as another NS for the domain - anything you create on your own NS will need to be the same on the 2 servidorwebsite.net NS.

Are you sure you have no means to add any records to those servidorwebsite.net DNS servers?

Also how many IP addresses did you get with your VPS? If you must run your own NS then you will need at least 2 IP addresses - preferably on different subnets. They can however both be on the same VPS - or you could BIND on your VPS and run up another nameserver with one of the many inexpensive DNS providers.

I'll take a closer look at your config files and see if we can at least get your VPS resolving the domain within itself. Once that is working we can worry about getting it working externally :D


EDIT-----
By the way, reverse DNS is already setup for your IP. Use the dig -x 200.160.239.84 command to view it.

```

crypto@ubulaptop1204:~$ dig -x 200.160.239.84

; <<>> DiG 9.8.1-P1 <<>> -x 200.160.239.84
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41666
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;84.239.160.200.in-addr.arpa.    IN    PTR

;; ANSWER SECTION:
84.239.160.200.in-addr.arpa. 86400 IN    PTR    tincgaming.com.

;; AUTHORITY SECTION:
239.160.200.in-addr.arpa. 86399    IN    NS    ns1.homehost.com.br.

;; Query time: 960 msec
;; SERVER: 192.168.1.67#53(192.168.1.67)
;; WHEN: Sun Jul  1 03:21:27 2012
;; MSG SIZE  rcvd: 106

```

---

### Post by Lico on 2012-06-30
Cryptotheslow,
i'm kinda sure that i can't add records to servidorwebsite.net's DNS servers... I could open a support ticket to my service and try to ask them to do it but I think the awnser will be negative... While browsing the VPS service provider website i've found a quite weird thing that i screencapped and will attach to this post. what could they mean by 5 additional IPs? Hmmm...

I have only one IP address on my VPS currently, and i'm really, really confused about what is happening. In a worst case scenario i'll transfer my domain to dyndns and pay their annual fee... if that would solve my problem of course... 
I don't know, i'm tottaly lost here. i'm very grateful you are helping me, THANKS A LOT!!


edit: That's nice! but does that mean my configuration is partially correct or that my provider did this automatically when i requested them?

---

### Post by cryptotheslow on 2012-06-30
The 5 additional IPs most likely means that they have assigned a /29 subnet to your VPS.

This means a section of 8 IP addresses in total.

Submit a ticket and ask them to tell you:
1. What your useable IP addresses are for hosts
2. What your subnet address is
3.  What your subnet broadcast address is
4. What your netmask should be

I think the answers you will get will be:
1. 200.160.239.81 - 200.160.239.86
2. 200.160.239.80
3. 200.160.239.87
4. 255.255.255.248

But ask so we are sure :)

As your server is already on 200.160.239.84 you have 5 of your 6 useable IPs still available.

Regarding the reverse DNS thing - it means that when your provider assigned your IP addresses to your VPS they setup the reverse DNS for it - probably automatically. As they control the reverse DNS for that IP range you cannot manage it yourself unless they delegate control for your subnet to you. It is probably not necessary to worry about reverse DNS at this point, it only really become a worry when it comes to SPF records for mail.

So get the above answered and let's get your forward NS resolution working first. Then once that is working we can sort out the reverse NS if necessary (I don't think it will be).

EDIT-----
Oh and you wouldn't necessarily have to transfer your domain to use a managed DNS provider to do your DNS. You would just take the managed DNS provider's service, use their web interface to add MX / A etc records and get your current domain provider to amend the NS records on your domain to point to the DNS service provider's NS servers.

Plenty of options here. DNS can be a headache when you first start to get into it :D It's logically simple once it clicks though :D

---

### Post by Lico on 2012-07-01
Sorry for the delayed response!!!
I've sent the VPS service a ticket asking the questions you posted and will probabbly have it answered in 4 hours or so (at about 7 am here) so it'll take some time :P

About the reverse DNS, thanks for clarifying that (and everything else) to me!
You're being a light in the end of a long, long tunnel! Thanks!

---

### Post by cryptotheslow on 2012-07-01
Don't worry about the delayed response - I slept too :D

Anyway here is a revised working db.tincgaming.com zonefile configuration for you:

```

;
; BIND data file for tincgaming.com
;
$TTL 14400
@ IN SOA ns1.tincgaming.com. indo.tincgaming.com. (
 2012063003 ; Serial
 7200 ; Refresh
 120 ; Retry
 2419200 ; Expire
 604800 ) ; Negative Cache TTL
;
@ IN NS ns1.tincgaming.com.
@ IN NS ns2.tincgaming.com.
tincgaming.com. IN A 200.160.239.84
localhost IN A 127.0.0.1
@ IN MX 10 mail.tincgaming.com.
ns1 IN A 200.160.239.84
ns2 IN A 200.160.239.84
www IN A 200.160.239.84
mail IN A 200.160.239.84
ftp IN A 200.160.239.84
tincgaming.com. IN TXT "v=spf1 mx mx:tincgaming.com -all"

```

I added it on to my lan BIND server to test it:
```

crypto@ubuserver:/etc/bind$ dig tincgaming.com any

; <<>> DiG 9.7.0-P1 <<>> tincgaming.com any
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11101
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 3

;; QUESTION SECTION:
;tincgaming.com.            IN    ANY

;; ANSWER SECTION:
tincgaming.com.        14400    IN    TXT    "v=spf1 mx mx:tincgaming.com -all"
tincgaming.com.        14400    IN    MX    10 mail.tincgaming.com.
tincgaming.com.        14400    IN    SOA    ns1.tincgaming.com. indo.tincgaming.com. 2012063005 7200 120 2419200 604800
tincgaming.com.        14400    IN    NS    ns2.tincgaming.com.
tincgaming.com.        14400    IN    NS    ns1.tincgaming.com.
tincgaming.com.        14400    IN    A    200.160.239.84

;; ADDITIONAL SECTION:
mail.tincgaming.com.    14400    IN    A    200.160.239.84
ns1.tincgaming.com.    14400    IN    A    200.160.239.84
ns2.tincgaming.com.    14400    IN    A    200.160.239.84

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jul  2 01:58:25 2012
;; MSG SIZE  rcvd: 239

```

You might want to just verify that SPF TXT entry is what you require as I amended it in the process of getting your zonefile to work.

Let us know how you get on :D

---

### Post by Lico on 2012-07-01
IT WORKS!!!!
Man, cryptotheslow, I LOVE YOU!
today I studied more about DNS and about how it works and tried modifying the file more but to no avail! You saved me so hard! I can't thank you enough! And my VPS service provider still hasn't answered!
Thank you very very much!!!
It's extremelly hard to find someone kind and patience with the noob kinds like me!
You have my gratitude!!!!
Lico

---

### Post by cryptotheslow on 2012-07-01
No problem at all :D These forums have helped me out many many times, it's nice to be able to give a little back. I'm a newb myself compared to most people on here, I just happen to have had a few VPSs, run some webhosting and been through through the basics of learning DNS stuff (I am by no means an expert!!). 

If you decide to continue to run your own DNS on this server then you will need to:
1. Configure one of your additional IP addresses onto the network interface of the VPS
2. Configure BIND to listen on both IP addresses and  using the 2nd IP as a secondary server
3. Update your zone file so that ns2.tincgaming.com resolves to the additional IP address
4. Get your provider to remove their NS records from your domain record and replace them with your ns1 and ns2
5. Get your provider to update the DNS glue records to resolve your ns1 and ns2 with the domain registrar

"Glue" records are required when the NS records for a domain are within that same domain. In order to avoid circular lookups the registrar needs to be able to resolve the IP addresses for the nameservers.

This explains it better than I can:
 [http://faq.domainmonster.com/dns/glue_record/](http://faq.domainmonster.com/dns/glue_record/)

If your NS IP addresses are in the same subnet you will get warnings when you run some online DNS setup checking tools. This is because according to the RFC standards the two nameservers for a domain should be on separate subnets and ideally geographically separate. However, that does not stop things from working when both IPs are on the same machine or subnet.

Oh - and you can delete your reverse lookup zone configuration. The only time it is meaningfully used is for mail SPF reverse lookups. Your MX IP already reverses to tincgaming.com and you have a tincgaming.com SPF record in your zone file - so it should be fine.

Have fun and let us know how you get on :D

---

### Post by Lico on 2012-07-03
Thank you very much, everything is working fine and i'll soon configure a new IP on the DNS! I owe you!
Lico

---

