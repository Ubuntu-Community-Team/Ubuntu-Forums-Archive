---
title: "Confusion concerning static versus dynamic ip"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Lakeside on 2008-10-28
Well I`ve been reading a few online guides about setting up my server.
The more I read the more confused I get. It is suggested it is good to have a dynamic ip (so the ip can resolve to an actual address..) So I got one (dynamic ip from DynDNS, let`s say it`s something like this:
Snapwebs.selfip.com).  Then I read here, that it`s good to have a static ip:  [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3) (I`ve also read that I could ask my isp to give me one, but that they usually don`t want to or will charge big $ for that). Then there is mention of `DHCP` etc. I`ve already entered the info from DynDNS (host, username, password) into my router, as well as portforwarding www at port 80 (just read to do that, not even sure about that). I am just confused, could someone please straighten me outÉ

---

### Post by Amorget on 2008-10-28
What are you trying to get your server to do?  Dynamic IP addresses are assigned via DHCP (that is what the D stands for, Dynamic Host Configuration Protocol), a static IP means you need to put all that information in.

---

### Post by Lakeside on 2008-10-29
> What are you trying to get your server to do?...
I don`t know anymore :-s. I only know that a dynamic ip means I can type in a web address instead of an ip..to get my website (I think) and that when I am installing Ubuntu server edition from a cd, it gives the option to pick dhcp: `The installer checks the installation CD, your hardware, and configures the network with DHCP if there is a DHCP server in the network`: (umm..what network, where, how would know if I had dhcp in my network, and if I get it, does that mean I automatically have dynamic ip and don`t have to get one from DyDNS

---

### Post by techstop on 2008-10-29
If your server is at home, when it comes down to it, you don't get to choose static between static and dynamic IP addresses, your ISP does. 

In Australia at least, most ISPs give out dynamic IP addresses, so you need to use the services of something like DynDNS so that when you type in a URL to access your web server, you get directed to the correct dynamic IP address for your server.

If you are fortunate enough to have a static IP address, you don't need to bother with all of that.

As you've said your ISP charges big $ for a static IP, then I guess you are forced to use DynDNS.

Also complicating the matter is that your server will have an IP address for its network card on your local network, and your router will have two IP addresses (one for the internal network, and one public address.

Just stick with the DynDNS setup. Here's a KB article, you've probably seen it;

[http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html](http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html)

---

### Post by Amorget on 2008-10-29
So you are trying to make a web server?  Here is what I would do... set the server to a dynamic IP address, set the router that you have to give that server a "static" ip address (meaning you pick the IP address, set it outside the range of available addresses, mine is 192.168.x.200), forward port 80 that that IP address.  Then you need to figure out what address your router is getting that is accessible from the outside world (normally you go into the setup and find the WAN IP address), and set that to the address over at DynDNS.

---

### Post by Lakeside on 2008-10-29
First off, I want to thank you both for your posts just now, and I think I should go to bed (lol) and give them the proper reading they deserve, when I can think clearly (tend to spend late nights trying to learn everything, so my post responses are getting...muddled :) ) TTYL in the morning (or maybe, `nightime` in Australia, eh É (sorry, what a question mark appears with my keyboard, a linux bug no doubt, sigh)

---

### Post by unutbu on 2008-10-29
Lakeside, I think a picture might be helpful:

```

Outside world <-------------> Your Router <---------> Your machine
                   ^                           ^
                   |                           |
               Choice A                     Choice B

```
Choice A: Use a dynamic DNS service or have your ISP give you a static (external) ip.
Choice B: Use DHCP or use a static (internal) ip

Amorget is recommending that you use a dynamic DNS service for Choice A
and a static (internal) ip for Choice B.

Between your router and your machine, your machine will have an internal 
IP address which begins with 192.168.xxx.xxx.

The outside world does not talk directly to your machine, instead, 
the outside world only sees your router. 

Your ISP will assign an external ip address to your router. 
You can find out what your external ip addrres is by going to [http://whatismyip.com/](http://whatismyip.com/)
(It could be something like 72.65.xxx.xxx)

In most cases for home users, your ISP is going to assign you a different 
ip address each time you connect. You are not given a static (external) ip.
This is why you would then need a dynamic DNS from some place like [www.dynDNS.com](www.dynDNS.com) or [www.no-ip.com](www.no-ip.com). (Both websites offer a free dynamic DNS).

---

### Post by Amorget on 2008-10-29
That is a very good explination, unutbu!

I am recomending a "static" IP address for your internal server assigned via DHCP from your router.  This will make it so the router always knows which machine is your server so it routes traffic correctly, as if you leave it dynamic it could change, so that "static" port forwarding you have setup would fail.  That is what I did to access my machine via remote desktop from the outside world.

---

### Post by Lakeside on 2008-11-04
Whoa! I just noticed these new posts, and should read in the morning, when I`m awake :) (and I had now internet connection for over 6 days, until now). Thanks for the helpful replys though.

---

