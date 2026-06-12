---
title: "Anonymous DNS servers"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by roodypoo on 2012-04-21
Would someone smarter than myself tell my if the DNS servers here

[Public Tier 2 Servers]("http://www.opennicproject.org/publictier2servers") 

That are marked "no logs" are effectively anonymous?

If not, anyone know a solution?

---

### Post by M!K3_$ on 2012-04-21
All it means is that the DNS server doesn't keep logs (apparently).

That website also has a "Anon logs?" column for all their listings.



You would probably be better off contacting the administrators if you really wanted to know.

---

### Post by SeijiSensei on 2012-04-22
By default servers running bind9 don't log queries.  On any busy server it would generate huge logs that would be onerous to deal with.

One way you can keep your requests private is to run your own DNS server.

---

### Post by roodypoo on 2012-04-22
If the DNS server does not keep logs would it be considered anonymous?

Also, I read here

[http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/](http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/)

And it still uses the ISP servers. Is there a way to create a completely local DNS?

---

### Post by SeijiSensei on 2012-04-22
There's no requirement that you use forwarders as that example does.  Without forwarders defined, a request for host.example.com will be sent first to one of the seventeen root servers that handle the "com" top-level domain.  The root will reply with the address of the servers that are authoritative for the example.com domain.  Then one of those servers is queried to resolve host.example.com.

If the roots keep logs then every request in the world would be logged, and the logs themselves would run into the terabytes.  The administrator of the nameserver for example.com could also keep logs of the IP addresses making queries.  In bind9, you can enable query logging by adding a configuration option to named.conf as described [here]("https://help.ubuntu.com/community/BIND9ServerHowto#Logging").  By default, this log isn't activated in the Linux distributions I've used, again because the logs generated could quickly become huge.

So the short answer to your question is that it's impossible to know who might be logging your requests, and there's little you can do about it.  Running your own server provides the greatest amount of privacy.  If your concerns are about things like logging requests to thepiratebay.com or to pron sites, you need to relax a bit.  No one is really going to care so much about you that they would investigate such things.  If you're running torrents, your IP address appears on the tracker; DNS has nothing to do with that.  If you're living in a country where Internet surveillance is part of a system of overall political repression, you should consider something like [TOR]("http://www.torproject.org/").

---

### Post by roodypoo on 2012-04-22
Thank you Sensei.

I might be a bit on the paranoid side, but I am just looking for the greatest amount of privacy possible. I know that nothing is perfect.

Actually using TOR had led me to these thoughts as the greatest risk (I think) to using TOR seems to be DNS leakage. Then I got to thinking about normal Internet usage. 

Who knows who logs what but just imagine what kind of profile you could build on someone if you knew all their Internet request, Credit Card usage and Cell records. To me it's scary. I don't want to marketed to every second I'm alive by more and more clever programs. I just want to stay as anonymous as possible.

Have you ever seen the move [The Game?]("http://www.imdb.com/title/tt0119174/") He takes a survey and they can guess every move he is going to make based on his answers. I'd bet looking at logs of a person that becomes a very real possibility.

---

### Post by SeijiSensei on 2012-04-22
I use the AdBlock Plus and Ghostery plug-ins for Firefox to keep my browsing habits from being shared with advertising networks.  I think things like "tracking cookies," which Ghostery blocks, are a bigger threat than DNS queries.

---

### Post by I2k4 on 2012-04-22
You might want to look into this:

[https://proxify.org/](https://proxify.org/)

Simple and seems to work well.

---

