---
title: "Image caching"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by keith.eckstein on 2008-09-01
I am just re-building my home network.

My main machine runs Ubuntu 8.04 and works fine.  It is connected to a switch.  Also connected to the switch is a machine (with 2 network cards), that runs Xubuntu (working great), which runs Firestarter to give me a firewall (that I can understand) and share my internet connection (broadband/ADSL).

The Xubuntu machine (which I'll call my server), also runs DNSMasq which gives me a massive speed improvement for the internet.

What I want to do is install something on the server (the machine running Xubuntu) that will cache images from frequently accessed websites (logos etc.) to further speed up internet access for any clients on the network (it seems silly to re-download the images and logos from this site every time I visit, for example) - don't download porn so have no security worries about keeping copies of image files.

Is there an easy way to get the server (the machine running Xubuntu) to cache any images (and forward them to network clients) that get downloaded as part of normal web browsing (I, like most others, spend 80% of my time on the same 20% of websites)?

I have looked at Squid but it seems overkill for a simple 4 client network - are there any alternatives (just as DNSMasq is a great alternative to BIND?)

Any help would be gratefully received - if I could get this working, then I could help spread the Ubuntu word amongst the English community in Brittany, France (where I now live) - we all suffer from slow internet connections (it's a rural area) and most of seem to have old boxes we could re-use as firewalls, Internet connection sharing, DNS caching and image caching.

All the best

Keith

---

### Post by gmoney on 2008-09-03
Here's a couple of links that have alternatives to Squid:

[http://httpd.apache.org/docs/2.2/caching.html](http://httpd.apache.org/docs/2.2/caching.html)

[http://www.web-cache.com/projects.html](http://www.web-cache.com/projects.html)

Also, you can increase your browsing speed by using Swiftfox, which is an optimized build of Mozilla Firefox. Swiftfox has builds for both AMD and Intel processors and is based on the most cutting edge Firefox source code available. The website is [http://www.getswiftfox.com](http://www.getswiftfox.com)

---

### Post by keith.eckstein on 2008-09-04
**Gmoney** - thanks for your response - I'll take a look at Swiftfox (am hoping that all my current extensions will work with it) - what I'm really looking for is a simpler alternative to Squid - it's sad to say but I used to have a very simple caching program running on an NT4.0 box that was my internet gateway - I can't remember its name but it certainly did the job.

I really just looking for something to cache images/logos - Firestarter does the firewall stuff; DNSmasq does the DNS caching; AdBlocker (on Firefox) speeds up site loading - it just seems silly to download the same website logos every day - if I could just find an easy and friendly alternative to Squid to cache these images permanently (and also prefetch links) - I'd be in heaven.

Anyway - greetings to all from rainy Brittany, France - hope someone can suggest a solution for me.


All the best

Keith

P.S.  I have thought about not clearing my cache in Firefox but that seems a bit of a cheat???

---

### Post by hyper_ch on 2008-09-04
squid would be my answer also... there's a lot of documentation out there to set a caching proxy... I'm sure you can get it to work.

---

### Post by Dr Small on 2008-09-04
You need Squid as a Cache Proxy server. I don't think it would be overkill. I use it to boost my speeds on the network, and it is highly configurable. Looks like Squid is what you need.

**Edit**:
I followed this guide to get Squid setup, and it worked great for me:
[http://ubuntulinuxhelp.com/speed-up-and-improve-web-surfing-with-an-ubuntu-squid-server/](http://ubuntulinuxhelp.com/speed-up-and-improve-web-surfing-with-an-ubuntu-squid-server/)

---

