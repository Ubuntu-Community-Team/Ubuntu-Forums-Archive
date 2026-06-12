---
title: "Why are thumbnail images saved in a subdomain or separate domain?"
date: 2010-11-25
forum: Programming Talk
---

### Post by ZaHACKieL on 2010-11-25
Hi everyone. I've seen that in lots of websites they keep their thumbnail images in a subdomain or different domain. For example, in Digg they keep them in cdn2.diggstatic.com , in Reddit they use thumbs.reddit.com, in IMDB ia.media-imdb.com, in Blogspot 2.bp.blogspot.com , and so on.

I'm just wondering why they do that and just not keep a thumbs folder(s) inside their domain?

I hope this is not a stupid question ^^

Thanx!

---

### Post by ZaHACKieL on 2010-11-25
I'll try to answer myself by asking...does it have to do with Content Delivery Network?

---

### Post by ZaHACKieL on 2010-11-26
Again, to answer myself, I can see this technique is used due to the connections limits the browsers have when connecting to the same domain, so, if you use subdomains or different domains for your static content you will trick the browser to open more connections for your website, decreasing the website loading time by these means.

Maybe I'm talking something everybody knows but I'm telling this because for me the thread is solved =]

Cheers

---

