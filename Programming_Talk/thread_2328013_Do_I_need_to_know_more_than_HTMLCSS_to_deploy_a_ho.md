---
title: "Do I need to know more than HTML/CSS to deploy a hosted website?"
date: 2016-06-16
forum: Programming Talk
---

### Post by cblnchat on 2016-06-16
Hey there,

Hopefully I worded that title well enough.

I'm currently teaching myself HTML/CSS (and then Sass...whatever that is) and realized that I have no idea if I have to know any PHP or other back-end languages to get a website running if I buy server hosting, from bluehost.com for example.

Thanks for any help

---

### Post by TheFu on 2016-06-16
No, but you´ll want to limit the site to static content and ensure that someone is patching all the software used weekly.

---

### Post by cblnchat on 2016-06-16
Being pretty new to this, static means...a site that doesn't change much, or not many animations and fancy stuff within the site?

---

### Post by TheFu on 2016-06-16
> **cblnchat said:**
> Being pretty new to this, static means...a site that doesn't change much, or not many animations and fancy stuff within the site?

It means none of the files used to create the site change automatically and that no DB is used on the back end. *Fancy stuff*, as you say, usually requires a program and DB.  However, there are ways to trick people into believing a static site is more complex than it really is.  For folks like you and I, perhaps the best solution for a website that doesn´t look static, but is, would be to use a static-site generator.  **webgen** is one, but there are at least 20 others.  

Search ¨webgen vs¨ to see some options.  Alternativeto.net is another place to look and there´s freecode.com/org (I don´t recall).

Off topic stuff:
My blog is ¨fancy¨ because it is a Ruby-on-Rails webapp with a DB back-end (and a reverse-proxy/load balancer on the front-end), but there are lots of blogs that do almost all the same things without the DB back-end and ruby programming using static website generators. Comments are displayed by disqus - those all happen off your site. There is a trade-off, privacy. Disqus gets to see all the traffic to your site, so it is **privacy sucking** in my book, but if you aren´t prepared to run a fairly secure comment tool yourself, but still want to allow comments, it is not a bad choice.  Most visitors don´t care and some actually prefer for that to be used. Web analytics (as in google-analytics) is another outside service that many websites use.   I care more about privacy, so if I see that Disqus is used, I´ll blacklist the site at the network level to prevent my privacy from being taken.  For google-analytics, I just blacklist all the google stuff (about 30 domains).  I´m different than most. You shouldn´t worry about people like me - unless privacy is very important to you as well.

---

### Post by gordintoronto on 2016-06-17
Many web sites are little more than online brochures, and HTML is all you need to build such a site.

---

