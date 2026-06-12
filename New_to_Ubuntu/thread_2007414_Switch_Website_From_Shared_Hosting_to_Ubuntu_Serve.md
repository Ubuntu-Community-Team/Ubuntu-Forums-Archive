---
title: "Switch Website From Shared Hosting to Ubuntu Server?"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by ergophobe on 2012-06-20
Hi,
 
I'm considering running an Ubuntu server to host a website, since our current shared server is performing poorly. I've set up Ubuntu server 12.04 LTS with SSH and LAMP, and read through several guides about setting configs, running updates, etc. Still not sure if it is a viable solution though, with the main concern being security. I have two questions:
 
1. We have 5 static IPs allocated by our ISP. Should we use a different IP for the webserver, from our current network?
 
The current network has a couple web cameras, a NAS, and some Windows 7 PCs used for web browsing... it wasn't set up with security in mind and probably isn't very secure. I'd like to avoid attracting attacks, but don't know if it would actually make a difference. The allocated IPs are sequential, i.e. x.x.x.10, x.x.x.11, etc.
 
2. Do shared hosts really provide better security than I would be able to? I've heard that before, but don't know if it's true.
 
We are going to be running an ecommerce site and installing a SSL cert for processing (but not storing) credit card numbers. Realistically, I will probably only check for updates every other week or so, and I saw an article on setting up emailing daily access log reports, which I might be able to check once a week, more frequently if it just takes a couple minutes. Unauthorized remote access to the server will not be a threat.
 
Any direct answers or links to good general information to consider are appreciated.

---

### Post by restorator on 2012-06-20
The short answer is if you don't know what you are doing, don't do it. Properly securing and maintaining an internet facing server is a job that doesn't stop. DO read up and study the subject and then setup a testing server to experiment with once you have a good understanding. You will likely find that the best thing for a live website, espeically an e-commerce site, is to have it inside a decent facility with high bandwith, good routers, staff on premises 24/7, redundant power systems and so on. This leads to the obvious. For a very small website, a GOOD host, not a cheap host, is the most efficient thing to use. The next step is a VPS so you have the benefits of full control of the system, but the security of the datacenter. And then on to a full private server when your needs reach that high. If you don't know what you are doing the odds of bad guys doing something is really high and can really cause you a variety of problems even in a datacenter, so imagine what could happen on your home network.

---

### Post by CharlesA on 2012-06-20
> **restorator said:**
> The short answer is if you don't know what you are doing, don't do it. Properly securing and maintaining an internet facing server is a job that doesn't stop. DO read up and study the subject and then setup a testing server to experiment with once you have a good understanding. You will likely find that the best thing for a live website, espeically an e-commerce site, is to have it inside a decent facility with high bandwith, good routers, staff on premises 24/7, redundant power systems and so on. This leads to the obvious. For a very small website, a GOOD host, not a cheap host, is the most efficient thing to use. The next step is a VPS so you have the benefits of full control of the system, but the security of the datacenter. And then on to a full private server when your needs reach that high. If you don't know what you are doing the odds of bad guys doing something is really high and can really cause you a variety of problems even in a datacenter, so imagine what could happen on your home network.
+1.

Set up a local VM and play around with it.

Read up on securing MySQL/PHP/Apache.

I would think Shared hosting has less security than a dedicated host cuz if one site on the host gets owned, the entire server is owned. Dedicated doesn't have the problem cuz there is usually only one site per host.

---

### Post by ergophobe on 2012-06-20
Thank you for the responses and advice. I think we will just move hosts for now, and possibly go with a VPS (maybe go to dedicated if it works out). Feel free to PM your good/bad host list if you have experience with a couple.
 
Also, going to set up a webserver on a separate external IP from our current network to host a non-critical site to learn/play with.
 
Thanks again.

---

### Post by restorator on 2012-06-20
There are a lot of good and a lot of bad hosts. I would go to webhostingtalk.com and poke around in there for reviews and advice and some change quality both up and down over time. There also have advertising forums where you can find decent deals, just do some research on the host before you leap. With little to go on for your needs but from my past experience, I would guess that a small VPS with at least 1gb ram would probably meet your current needs and cost you about $20and up a month at an ok host.  If you setup a test server and/or go with a vps, you will find yourself at the webhostingtalk.com website very often. A lot of good advice on webservers there.

---

