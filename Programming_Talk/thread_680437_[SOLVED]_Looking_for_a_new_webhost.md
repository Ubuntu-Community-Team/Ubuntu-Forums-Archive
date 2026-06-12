---
title: "[SOLVED] Looking for a new webhost"
date: 2008-01-27
forum: Programming Talk
---

### Post by mssever on 2008-01-27
I'm looking to switch webhosts, and I'm looking for recommendations. After being burned by my current host (IX Webhosting), which I found by searching and reading reviews, I don't particularly trust Google. It appears that the reviews I read were highly inaccurate--perhaps paid for by the web host.

Here are my requirements:[LIST]
[*]PHP 5
[*]Apache with mod_rewrite
[*]MySQL; a sufficient number of databases allowed
[*]PHPMyAdmin
[*]Multiple domains hosted on a single account
[*]Unlimited (or practically unlimited) subdomains
[*]Highly reliable; my current host's database server frequently goes AWOL, making my websites unaccessible. The only thing I can do is return 500 Internal Server Error[/LIST]Features that would be nice to have, but aren't strictly necessary:[LIST]
[*]Ruby; I'm starting to dabble with Rails. If I ever get something useful, I'll want to host it publically
[*]Python; Why not? I might have a use for it some day, and there's really no reason NOT to support Python or any other common language
[*]Shell access[/LIST]Does anybody have any recommendations?

---

### Post by bdlang on 2008-01-27
I've used mediacatch.com for a couple of years now, they haven't let me down.

Everything you've requested they offer, including Ruby on Rails & JSP if you want it as well. They're great to offer custom packages and tailor the hosting to exactly what you want. Haven't had an issue with downtime.

---

### Post by Vadi on 2008-01-27
Network Redux. They have an excellent deal, and equally excellent support - as an added bonus, they're very open-source friendly and host many projects for free.

I highly recommend them.

---

### Post by pmasiar on 2008-01-27
Is it for a personal development, or for production server for a small company/startup? Do you have a budget? Because as they say, you get what you paid for.

---

### Post by Cappy on 2008-01-28
I've used site5.com for 2 years now and I've always loved it. I host my site [http://www.boundlesssupremacy.com/](http://www.boundlesssupremacy.com/) (and a few more!) on it.

It supports everything you mentioned and MORE. For instance, you can pick whether you want a folder to run with php4 or php5. Best of both worlds.

They offer rails and python. They offer shell access but you will have to email and ask for it for security reasons (every host I've ever had has done this).

Reliability is proven:
[http://florida.websitepulse.net/uptime/D5774I9161.html](http://florida.websitepulse.net/uptime/D5774I9161.html)
This is the shared hosting server my websites are on. I don't remember where I got this link but there is/was a listing like this for all of site5's servers.

Also, you can edit any of the domain's DNS Zone. For instance, mail.boundlesssupremacy.com could resolve to another IP. My previous webhosts didn't let me do that.

---

### Post by RedNikon on 2008-01-28
[NearlyFreeSpeech.NET]("https://www.nearlyfreespeech.net/") they are simple, feature rich web host. Also they only charge based on what you use, with that said their price are still extremely competitive.

Also the support all of the things you listed earlier.

---

### Post by mssever on 2008-01-28
> **pmasiar said:**
> Is it for a personal development, or for production server for a small company/startup? Do you have a budget? Because as they say, you get what you paid for.

This is for hobby sites that I make no money from. So I don't want to pay very much, nor do I get much traffic.

---

### Post by LaRoza on 2008-01-28
> **mssever said:**
> This is for hobby sites that I make no money from. So I don't want to pay very much, nor do I get much traffic.

Would it be possible to host it yourself at all?

It is unlikely that is a good option, but you have the ultimate flexibility then.

---

### Post by Acglaphotis on 2008-01-28
One,com is cheap, i just bought my domain (and hosting) from them.

---

### Post by Vadi on 2008-01-28
Google Pages? Completely free there. Although it's restrictive as to how can you design the pages.

---

### Post by ThinkBuntu on 2008-01-28
Get **Hostgator**'s $9.99 per month account. It has Ruby, RoR, Python, etc. although I haven't tried these languages on the host. PHP5 is there, you just have to insert some line into a .htaccess or similar initialization file. There's a post floating around the interwebs about it. Anyway, PHP5 works fine there. MySQL works great, unlimited domains and subdomains, really no complaints. Uptime is excellent, and I haven't had any logged downtime on either my site or my clients' sites. They guarantee 99.9% uptime for all $9.99+ accounts.

Only problem I've had is them changing configuration once, unannounced. When this happened, my CSSForums were down for no reason. Changing a config file in the forum from "mysql" to "mysqli" fixed the problem, but I was annoyed.

Also, coupons are floating around that will give you a $9.98 discount for your first month. And on top of all that, they're snappy with DNS changes and require no startup fee.

---

### Post by mssever on 2008-01-28
> **RedNikon said:**
> [NearlyFreeSpeech.NET]("https://www.nearlyfreespeech.net/") they are simple, feature rich web host. Also they only charge based on what you use, with that said their price are still extremely competitive.
That looks like a great deal. I have a couple of questions, though. They say that since they don't provide FastCGI, Rails performs horribly. Do you have any experience with whether Rails performance is acceptable for a small-time site? Also, since they don't support SSL, have you had any need to work around that limitation? If so, what did you do?
> **LaRoza said:**
> Would it be possible to host it yourself at all?

It is unlikely that is a good option, but you have the ultimate flexibility then.
I have satallite Internet, which delivers horrible performance. I do host some things myself (generally for my use only when I'm away from home), but accessing them is a chore due to speed issues.

----

Thanks for all the suggestions. I'm looking at all of them. Since I haven't made up my mind yet, I'm still open to suggestions.

---

### Post by ssam on 2008-01-28
[http://www.slicehost.com/](http://www.slicehost.com/) starts at $20/month you get root access to a xen virtual server with a choice of distros.you can install what ever you want on it.

---

### Post by RedNikon on 2008-01-28
> **mssever said:**
> That looks like a great deal. I have a couple of questions, though. They say that since they don't provide FastCGI, Rails performs horribly. Do you have any experience with whether Rails performance is acceptable for a small-time site? Also, since they don't support SSL, have you had any need to work around that limitation? If so, what did you do?

I haven't played around with Rails so I wouldn't know, how ever if you want I can give you access to one of my play sites and you play around with it yourself just to test it. Just PM me if you want to take me up on the offer.

As far as ssl support I haven't had the need for it. Not sure if you read why they don't support it, I find it a good enough [reason]("https://www.nearlyfreespeech.net/about/faq.php#Static"). But also note that they are currently in the process of find a work around or providing the service if they can find some why to stick within their policy.

---

### Post by pmasiar on 2008-01-28
webfaction is also highly recommended host.

---

### Post by mssever on 2008-02-10
Thanks for all the input, everyone. I've just switched to NearlyFreeSpeech.NET.

---

