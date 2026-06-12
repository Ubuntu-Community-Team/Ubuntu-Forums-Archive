---
title: "Apache2 and CSS images issues. Looking for help."
date: 2011-04-05
forum: Programming Talk
---

### Post by garfonzo on 2011-04-05
Hey Folks:

Here is my situation: I have a server running a company website. I had to get it up and running fairly quickly so I wrote every page in raw HTML. Now that I have had the time to breath, I have re-written the whole website and am ready to re-deploy it (the other reason for re-writing it was for future plans to substantially increase the website's content and functionality). 

The problem I am having is that any image referenced in my CSS style sheet will not load, but any image referenced within a webpage (a <img> tag) works fine. The weird thing is that all images are located in the same spot ("media/img"). 

Why would the <img> images show, but not the CSS images? I'm confused! 

One relevant point is that the new website is driven by Django, so instead of using img links of: ```
<img src="img/my_image.jpg">
``` I use complete paths: ```
<img src="http://www.mysite.com/media/img/my_image.jpg">
``` I even ricght-clicked an image that *was* being displayed properly, and confirmed that the address is *identical* to the addresses for the CSS images. 

Anyone have any ideas?

---

### Post by garfonzo on 2011-04-05
OK -- I think I have other problems which make this thread unnecessary. 

Site Admins -- can you delete this thread? 

Thanks.

---

### Post by johnl on 2011-04-05
Hi,

It depends on how you have configured your webserver to serve django.  django does not serve static/media content;  you need to use another webserver to do that.  

If you are using apache/mod_wsgi (which I found to be the least confusing way to deploy django), you can follow the instructions here:
[deploying with modwsgi](http://docs.djangoproject.com/en/1.3/howto/deployment/modwsgi/).

As an aside, I thought the hardest thing to do with django was to actually deploy a project with it :)

---

### Post by garfonzo on 2011-04-05
> **johnl said:**
> Hi,
As an aside, I thought the hardest thing to do with django was to actually deploy a project with it :)

That is precisely what I am finding too!

I don't have the option to serve media on a seperate server, so I need to figure out how to make it all work on one. That tutorial you linked to references how to do this so I may try WSGI.

---

