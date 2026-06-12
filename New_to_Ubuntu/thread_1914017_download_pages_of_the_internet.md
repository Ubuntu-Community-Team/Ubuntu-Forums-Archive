---
title: "download pages of the internet"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by vagelism on 2012-01-23
I need a light GUI program if is possible to download pages from internet from a root path and on...
for example all the links from /url/blabla/... and down...
If I remember correct in windows was one called getright or something like that.
Is it something similar to ubuntu?

---

### Post by sanderd17 on 2012-01-23
> **vagelism said:**
> I need a light GUI program if is possible to download pages from internet from a root path and on...
for example all the links from /url/blabla/... and down...
If I remember correct in windows was one called getright or something like that.
Is it something similar to ubuntu?

This is normally impossible. It's how private url's can't be tracked.

And why does it need to be a Gui tool? with wget, you can get a single page,and if you put wget in a script, you can get a list of pages, but there is normally no way to get all files under a certain url.

---

### Post by vagelism on 2012-01-23
I am sure there was a program in windows that did exactly this work.
Storing localy all the urls from one path and so on depending the depth the user wanted. for example 2 clicks from that page, 3 and so on.
So the result was to have all the public domain to your hard drive.
Thanks.

---

### Post by sanderd17 on 2012-01-23
> **vagelism said:**
> I am sure there was a program in windows that did exactly this work.
Storing localy all the urls from one path and so on depending the depth the user wanted. for example 2 clicks from that page, 3 and so on.
So the result was to have all the public domain to your hard drive.
Thanks.

ah, you mean a script that follows the links? that is possible. But I don't know a program that does it.

---

### Post by mocha on 2012-01-23
Did you look into httrack and the various GUIs it has?  My favorite is webhttrack.

---

### Post by Cheesemill on 2012-01-23
I also use webhttrack, but you should be aware that a lot of websites don't take kindly to being hammered in this way and will maybe limit access from your IP address.

---

