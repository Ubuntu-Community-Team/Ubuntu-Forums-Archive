---
title: "NameServer for Godaddy - Apache Please Help"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by justinram22 on 2008-10-10
Hello, I've been searching for this for the past 4 hours and i have just gave myself a headache lol, I have finally got it, so i can view my site via IP address from everywhere, now my question is, how do i make my domain name go to my site? like instead of [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/) it would be [http://www.mysitedomain.com/](http://www.mysitedomain.com/) I have looked into [www.DynDNS.com](www.DynDNS.com) but i have no clue how thats is supposed to work, or even if i need that for this.. im a 13 year old so sorry if im not understanding this stuff, but i'd really like to host my own site, instead of paying someone to do it for me, when infact i can do it myself lol; a step by step tutuorial would be nice

P.S. to forward your domain name or whatever in godaddy i need 2 nameservers...

Any Help would be greatly appreciated!

---

### Post by bodhi.zazen on 2008-10-10
If you purchased a domain name at godaddy, call tech support. They are very good and will walk you through the basic set up.

After you set up a domain it can take up to 24 hours for it to propagate through the system (ie it will not work right away).

---

### Post by cgkades on 2008-10-10
if you dont have go dady, i can probably walk you through dynDNS, thats what i use

edit after reading again: if you are going to host your own services, you need a nameserver on your end, and then one to forward to, the forwarding to is not the big deal, the complicated part comes in resolving hostnames to your site. i think godaddy can do this for you, they'll forward requests to your name server that you have set up with your local stuff. unless you are doing some more complex routing with NAT, you'll have to have your servers use real world ip's provided by your ISP, or run all your services off one server. you may want to look into using something like smoothwall to help protect your servers because unels you use a firewall or a router with NAT your servers are really exposed to attack

there are lots of tutorials out there on how to set up DNS. if you seriously cant find any, i'll look for some and post back the ones that look good

---

### Post by justinram22 on 2008-10-11
Ok, here is how far i got... lol i've been looking at some more tutorials, and i just keep getting more and more confused, it says i need 2 ip address to create 2 nameservers?? basically i need a dns1.domain.com and dns2.domain.com but i have no clue how to get that because i only have 1 ISP.. any help would be greatly appreciated!

---

### Post by bodhi.zazen on 2008-10-11
> **justinram22 said:**
> Ok, here is how far i got... lol i've been looking at some more tutorials, and i just keep getting more and more confused, it says i need 2 ip address to create 2 nameservers?? basically i need a dns1.domain.com and dns2.domain.com but i have no clue how to get that because i only have 1 ISP.. any help would be greatly appreciated!

What site are you using ? godaddy ?

If godaddy.com -> call their tech support, they are available 24/7 and will set you up.

Normally you need two nameservers if you are setting up your own DNS ... ?

---

