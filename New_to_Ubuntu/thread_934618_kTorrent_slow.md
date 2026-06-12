---
title: "kTorrent slow"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by ubunt2guy on 2008-09-30
is it normal that most torrents larger than 750mb take a couple days to d/l?

---

### Post by zephyrcat on 2008-09-30
You could try another bittorrent client, but I suspect the problem might be your ISP. What ISP are you using? Some throttle or cut off bittorrent.

---

### Post by ubunt2guy on 2008-09-30
> **zephyrcat said:**
> You could try another bittorrent client, but I suspect the problem might be your ISP. What ISP are you using? Some throttle or cut off bittorrent.

road runner

what do you mean "throttle or cut off bittorrent"?

---

### Post by aparigraha on 2008-09-30
First of all... how many people are seeding, and at what speeds?

[http://en.wikipedia.org/wiki/Bandwidth_throttling]("http://en.wikipedia.org/wiki/Bandwidth_throttling")

[http://www.azureuswiki.com/index.php/Bad_ISPs]("http://www.azureuswiki.com/index.php/Bad_ISPs")

RoadRunner is not on the list.

---

### Post by nowshining on 2008-10-01
throttle means that they limit the speed at which one may download torrents, ie: they limit torrent traffic...

Alas the slowness can be caused by several things:

A: isp as mentioned above
B: media companies - ur downloading from them or they are slowing ur downloading by more sophisticated software, machines, etc..
C: ur connection to the net isn't stable
D: person is uploading via dialup, limited upload, etc..

if on A and B, there are several things u can do:

A/B: get a firewall, i heard on 8.04 ufw is available...

If u don't have a firewall, I may be able to get u setup with some ips to block with iptabls, but i suggest reading up on the forums for modblock or mobblock or whatever and taking a look around the web about this stuff.. try bluetack.co.uk for a torrent site with some blocklists - they have a converter to convert to iptables rules if u want...

C: could be a number of things

D: u can only download as fast as the uploader allows, if the uploader is using dialup or equiv., and they don't throttle then u can only download at about 5-7 kb/s, if they throttle themselves so they can browse the web, etc.. then it could be throttled down to at around 3-4 kb/s...

However high speed uploaders are also more likely to throttle the speed as mentioned above...

edit: if u want i suggest arno-iptables-firewall for a firewall and if u do chose arno i can get u setup with some blocking ips :) it may take a bit to load if u want them all and some i'm not done adding, but once again I can set u up, but if u want the ips anyway and again all in iptables format, just email me at m

but fory email addy and i'll send it as an attachment 'cause it's at around 400kb.. :P

as for an iprules that may help in the future - these were for comcast, but may work for others at which comcast would reset the connection to the torrent and thereby cutting off the uploading/downloading of the item, i modified it for all ports.. :)

```
#Block comcast resets/bandwidth throttling but modified for both inbound and outbound for many ports., etc.. & so forth & for protection against reset attacks.

iptables -A INPUT -p tcp --dport 0:65535 --tcp-flags RST RST -j DROP

iptables -A OUTPUT -p tcp --dport 0:65535 --tcp-flags RST RST -j REJECT
```

edit2: oh yeah input is for them initiating a connection to ur computer from theirs and outgoing it for going from ur computer to the web, etc...

---

### Post by ubunt2guy on 2008-10-01
> **nowshining said:**
> throttle means that they limit the speed at which one may download torrents, ie: they limit torrent traffic...

Alas the slowness can be caused by several things:

A: isp as mentioned above
B: media companies - ur downloading from them or they are slowing ur downloading by more sophisticated software, machines, etc..
C: ur connection to the net isn't stable
D: person is uploading via dialup, limited upload, etc..

if on A and B, there are several things u can do:

A/B: get a firewall, i heard on 8.04 ufw is available...

If u don't have a firewall, I may be able to get u setup with some ips to block with iptabls, but i suggest reading up on the forums for modblock or mobblock or whatever and taking a look around the web about this stuff.. try bluetack.co.uk for a torrent site with some blocklists - they have a converter to convert to iptables rules if u want...

C: could be a number of things

D: u can only download as fast as the uploader allows, if the uploader is using dialup or equiv., and they don't throttle then u can only download at about 5-7 kb/s, if they throttle themselves so they can browse the web, etc.. then it could be throttled down to at around 3-4 kb/s...

However high speed uploaders are also more likely to throttle the speed as mentioned above...

edit: if u want i suggest arno-iptables-firewall for a firewall and if u do chose arno i can get u setup with some blocking ips :) it may take a bit to load if u want them all and some i'm not done adding, but once again I can set u up, but if u want the ips anyway and again all in iptables format, just email me at m

but fory email addy and i'll send it as an attachment 'cause it's at around 400kb.. :P

as for an iprules that may help in the future - these were for comcast, but may work for others at which comcast would reset the connection to the torrent and thereby cutting off the uploading/downloading of the item, i modified it for all ports.. :)

```
#Block comcast resets/bandwidth throttling but modified for both inbound and outbound for many ports., etc.. & so forth & for protection against reset attacks.

iptables -A INPUT -p tcp --dport 0:65535 --tcp-flags RST RST -j DROP

iptables -A OUTPUT -p tcp --dport 0:65535 --tcp-flags RST RST -j REJECT
```

edit2: oh yeah input is for them initiating a connection to ur computer from theirs and outgoing it for going from ur computer to the web, etc...


Thanks for the great post.  I always like to learn new things.

But i looked at my peers and most are from China/Japan/Philippines and seeding at around 1-11 KB/s.  But when I D/L something else around the same size a few min ago it D/L quicker because my peers were uploading/transfering quicker.  

-My question is that I thought you can D/L faster if you U/L more.  So should I upload faster/more or is it just a combination of more uploading and faster/better/more peers?  

-I have 20(36) peers in my current download.  Is that good?

---

### Post by nowshining on 2008-10-01
> **ubunt2guy said:**
> Thanks for the great post.  I always like to learn new things.

But i looked at my peers and most are from China/Japan/Philippines and seeding at around 1-11 KB/s.  But when I D/L something else around the same size a few min ago it D/L quicker because my peers were uploading/transfering quicker.  

-My question is that I thought you can D/L faster if you U/L more.  So should I upload faster/more or is it just a combination of more uploading and faster/better/more peers?  

-I have 20(36) peers in my current download.  Is that good?

again it depends on the uploaders speed :) ah! yes alas i forgot to add, are u using the default ports?? It's suggested not to use any default ports for torrenting and chose one up in between the 30 thousand + range... example: port:46112 :) and for uploading u do need open incoming ports...

and a direct answer to ur new Question is in general yes, pretty much and again the big media companies can cut u off, block download/upload slots, etc.. esp. on music/movies, etc.. so again it's highly suggested to get a blocker or else those may happen or u may get sued... and since RR is pretty much associated with the BIG media companes and they pretty much are one, i'd more more worried about that...

I used to have RR my self where I live - but it always went offline every now and then and i used to take 95% uptime when they told me as good (i called), but later found out that hey that's a lot of downtime.. :/

---

