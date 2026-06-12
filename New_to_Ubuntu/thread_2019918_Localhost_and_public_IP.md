---
title: "Localhost and public IP"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by newn on 2012-07-07
I'd like to keep one site for myself, as in testing, while another one, I'd like to set so that it would be seen publicly (basically one localhost site, and one 192.168.1.1 site) - is there a more straightforward  solution, or should I go with virtual hosts?

---

### Post by garyed on 2012-07-07
Why not just make a separate directory just for testing.
You can password protect the index file if you want an extra level of protection.

---

### Post by newn on 2012-07-07
> **garyed said:**
> Why not just make a separate directory just for testing.
You can password protect the index file if you want an extra level of protection.

 Well, that's a moderately good solution. I think I'd be okay with that. I'm pretty much looking to use it for web development. or learning web development anyway.

---

### Post by Bucky Ball on 2012-07-07
Just open the web dev tools of your choice, create pages and look at them locally in Firefox. Just don't post them to the server. Easy. 

When you're happy, post them to the web host for public perusal. This is rule of thumb way as otherwise you are uploading and downloading the html page everytime you change/want to change the page. Rubbish option when you are just putting it together. These could mean hundred(s) of up/downloads and the time spent doing it.

For consistency, you want the pages on the site to look similar design, right? Well, you get one well designed page together for your index.html and use that as a template for the others, just change text and pictures. ;)

---

### Post by newn on 2012-07-07
Actually I'm looking to work with PHP and SQL now, as HTML is only the basic form that my site is going to take, and which I already have. Except I need to work some more on the graphical design part, but that could be with no end - right? :)

---

### Post by Bucky Ball on 2012-07-07
If you mean locally, yes. You talking about PHPing with and an sql database on the web host server (not a local database)? ;)

---

### Post by newn on 2012-07-07
I'm talking about a local database - why rent when you can get it for free and without any ping? :)

---

### Post by Bucky Ball on 2012-07-07
Okay, so you are going to serve your public.html from your local computer ...

If everything is local I see no reason why you can't do everything you want to do. Just don't serve the test page, only the pages you want public. You can see and test everything with dev tools and web browser locally. 

Trust me, unlikely anyone is going to hit your web page without knowing it's there. You need to do stuff to get it on search engines and noticed and it will take sometime to propagate when you initially post the site. If you don't tell people the address, they ain't gonna find it in a hurry. It will take a long time to get rated anywhere near the top of a search; it gets ranked by hits (and/or deals with the search engine) and if it's never hit and you haven't paid to be boosted up the rankings it won't be easily spotted unless someone puts the address directly in the address bar. ;)

I'd post the site, work away, tell people where it is when you want them to visit ...

---

### Post by newn on 2012-07-07
Yes, that is correct - why is that bad?

---

### Post by Bucky Ball on 2012-07-07
> **newn said:**
> Yes, that is correct - why is that bad?

It's not if it suits your purpose. More work is probably all but you'll learn plenty. And security is entirely your responsibilty (so be especially diligent if you have other users on the LAN you're hosting your site to the WAN from).

Web hosts provide a lot of tools to make life easier (CPanel for one) but certainly not advocating you should use one. Another consideration is bandwidth. If your site is really successful could your bandwidth handle serving a thousand visits a day? ;)

---

### Post by newn on 2012-07-07
Well I love digging around and learning various things like how to set up a web server, etc.. I wouldn't mind reading some tutorials or guides or whatever along these lines to learn more and more advanced things about Linux administration. It's one of the things I am interested in... So that's a huge upside.

Also I'm the only LAN user over here, so no problems with that. I was thinking of using ISPConfig, but it's more for a commercial type of activities, so I skipped on it. Plus, I will learn more technical stuff.

I don't have any bandwidth limitations, so that's not a problem. :)

---

