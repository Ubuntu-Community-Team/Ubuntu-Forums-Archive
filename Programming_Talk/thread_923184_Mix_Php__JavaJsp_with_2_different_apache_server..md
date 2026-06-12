---
title: "Mix Php / Java/Jsp with 2 different apache server."
date: 2008-09-18
forum: Programming Talk
---

### Post by ierpe on 2008-09-18
We are using an application that manages blue tooth devices. This application is written in Java, and the cms associated to it is written in jsf(Java/jsp).
Their application is running with apache-ant. I've been adding some code to their web application to suit our needs, but their build is so that I cant add php to this server.

We need a different cms than their, and This one has to be programmed in php.

My question is the following:
If I have two apache running, the first one included in their application, and a second one for my php cms, will I be able to call a page located in their application from my php application?

I hope it makes sense, this case is weird to describe :p

---

### Post by PC-XT on 2008-10-03
You can usually use PHP's file functions like fopen to retrieve pages from other servers if you have the address (like you type in a browser.) I imagine that if you can get the page in a browser, you can get it with PHP's file commands. I haven't actually tried this myself, though, because the file functions on the servers I work with were set to not handle requests to other servers.

For submitting form information, this will work for GET requests, where the request is encoded after a ? following the url. POST requests would need some other method (I don't remember if one exists.)

---

