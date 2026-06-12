---
title: "Static ip address and self hosted name server...can it be done???"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by adamjedgar on 2013-11-26
Firstly, I apologise if this is a little disjointed. 

Whilst i am quite computer literate (spent a couple of years part time studying database administration, hardware and software applications) im relatively green when it comes to web hosting. I have set up my own Vm Virtualbox Ubuntu virtual server (LAMP). Configured some html and css on my real website hosted by crazydomains on one of their own servers such that, the website title logo is sourced via URL from the var/www/Images directory on my virtual ubuntu server here at home. Now i know for all you web tech heads out there, thats a simple exercise...however, whilst relatively problem free...it still took me about 1.5-2 hours to learn how to correctly code everything on the web host's server and setup permissions on my apache server at home. Thankfully, with some minor corrections i essentially got it to work relatively easily and after only my second attempt. The biggest issue was getting the image alignment correct (had to go negative 30px on the vertical alignment to get it up near top of web page).

_**Anyway...on to my question!**_

I have a static public ip address assigned by my ISP.

Is it possible for me to have my own www name server/s on my own ISP assigned static ip addresses or is this something that only an internet registrar can have??? (i know only a registrar is able to register domains but what about linking name servers with one's own static ip addresses???)

My reason for asking this question is as follows

I have just become a reseller. I notice that, whilst my supplier claims to provide awesome wholesale pricing, in reality their own retail store is constantly offering most products ON SALE...often at huge discounted prices (often barely above advertised wholesale rates). This is bloody anti-competitive if you ask me, however i notice it seems to happen with other registrars too...and frankly im unhappy with the idea of making $1 or $2 per month hosting web sites as a reseller...unless i quickly get tens of thousands of clients, id be better off on government handouts!!!

If i was able to link a www nameserver to my static ip address then** i could self host "small web sites**" as a reseller, rather than use my suppliers hardware, without having to pay for dns forwarding, or at the very least...try to find my own data wharehouse. I dont see the point in simply finding an alternative to my suppliers hosting because it seems that registrars charge more for dns forwarding than hosting (which i guess is to try to convince people to get hosting through same provider).

Now i know there will be those out there who will say...its not worth the security risks....blah blah blah... whilst i dont have a lot of experience, i do realise there are significant disadvantages to self hosting...however, this is all about learning how it can be done if you please!

cheers
adam

---

### Post by HeroOfCanton on 2013-11-27
Advanced apology accepted. :smile:

I'll hit what I can here for you.

#1. **Hosting reseller**  - You're correct. Not worth it. The time you spend answering questions  for your clients will NOT be covered by your $1 a month profit.

#2. **Pointing DNS to home IP** - Can you point a DNS towards your home IP? Yes. Should you? Read on...

#3. **Self hosting**  - I agree with the people who would say it's not worth the risks, but I  won't blah, blah, blah you with my opinion. It's unlikely you have the  upstream bandwidth or a friendly enough ISP to pull off being a host  from your house though. Could be wrong, but the chances are slim. I do host some small "sub domain" stuff from my home server without issue, but nothing that more than a few people have access to. Providing hosting for others is a big responsibility to take on.

I  like your "doing for the sake of doing" spirit and don't want to discourage you though! Have you  considered a virtual (aka cloud) server to start? They are pretty cheap  now-a-days. You can get a nice little personal linux machine running in  the "cloud". All of the same software learning experience, plus real  bandwidth and hardware that is scalable on the click  of a button. Plus, if it breaks in the middle of the night you get to call someone else! ;)

P.S. Study up on security if you're going to open your server to the world in any way. You WILL get intrusion attempts.

---

