---
title: "Caching Dynamically Served Images"
date: 2008-08-26
forum: Programming Talk
---

### Post by Lster on 2008-08-26
Hi everyone!

I'm coding an AppSpot application using GAE of course. Users are allowed to add their own avatars to their profiles and I have an address within my site called /getavatar?{id} with id the user id. I can quite easily get it to serve out the PNG images but everytime I refresh the page the images flicker slightly because they are not cached.

So my question is can I change certain information in the header to make the web browser cache them?

At the moment my code for /getavatar looks roughly like:

[PHP]
self.response.headers['Content-Type'] = 'image/png'
self.response.out.write(user.avatar)
[/PHP]

I've read up on some caching tips and it seems I need to change Expires or some other headers to certain values to make the browser cache them. I've tried all the different ways I can find and my results vary from nothing changing to making the images unloadable!

Any tips would be great! Thanks,
Lster

---

### Post by Lster on 2008-08-27
I've figured this kinda' out for myself now so I thought I'd share in the chance that someone might find it useful...

It seems to work at least partially although my browser does reload it quite often still (but it doesn't seem *so* often). The most useful thing in testing the cachability of images is probably:

[http://www.ircache.net/cgi-bin/cacheability.py](http://www.ircache.net/cgi-bin/cacheability.py)

The other thing I found useful was:

[http://en.wikipedia.org/wiki/List_of_HTTP_headers](http://en.wikipedia.org/wiki/List_of_HTTP_headers)

I simply set the Expires and Content-Type response headers and it seems better. Maybe someone has a better solution, because this is far from perfect and the cachability test still tells me it isn't good! ;) I think using other headers is recommended really...

---

### Post by skeeterbug on 2008-08-27
You could always use memcached.

[http://code.google.com/appengine/docs/memcache/usingmemcache.html](http://code.google.com/appengine/docs/memcache/usingmemcache.html)

---

### Post by Wybiral on 2008-08-29
> **skeeterbug said:**
> You could always use memcached.

[http://code.google.com/appengine/docs/memcache/usingmemcache.html](http://code.google.com/appengine/docs/memcache/usingmemcache.html)

memcache works great for server-side caching, but Lster is looking to tell the browser to cache an image.

---

