---
title: "Website question"
date: 2009-01-21
forum: Programming Talk
---

### Post by vhegos on 2009-01-21
Hi,

I am new to managing a webpage and have a question about how to ensure that the latest documents are the ones provided by the server when a request is made.  Specifically, suppose I have an html document that I update on a frequent basis, and viewers view this document on a frequent basis.  What do I need to do so that the viewer need not hit the refresh button each time they visit the page?  

Sorry if this is unclear.  It is the best way I know how to put it, and I don't quite know how to google the answer myself.  

Thanks in advance!

---

### Post by skullmunky on 2009-01-21
If everything works correctly, the user should always be getting the most recent version; you only see the cached version of a page if there isn't a more recent version on the server.

You can set meta tags to control the expiration time or set the page not to cache at all, so the browser will always download it even if there haven't been any changes. 

Actually maybe what you want is this: the user leaves the page open in the browser, and when there's a change to it, it refreshes automatically.  For example, a webmail program, or a stock quote viewer or something. 

In that case one way you can do it is again with META tags, using REFRESH.  

here's a handy list:

[http://www.i18nguy.com/markup/metatags.html](http://www.i18nguy.com/markup/metatags.html)

if only parts of the page are changing, the web2.0-ish way to do it is with AJAX or similar; use javascript to periodically send an XML request back to the server to check for new content, and update the page accordingly.

---

### Post by cl333r on 2009-01-22
Send all following headers:

// Set to expire far in the past.
Expires: Sat, 6 May 1995 12:00:00 GMT

// Set standard HTTP/1.1 no-cache headers.
Cache-Control: no-store, no-cache, must-revalidate

// Set IE extended HTTP/1.1 no-cache headers
Cache-Control: post-check=0, pre-check=0

// Set standard HTTP/1.0 no-cache header.
Pragma: no-cache

---

### Post by vhegos on 2009-01-22
Just what I needed.  Students may no longer claim they did not "see" the latest homework posted.  Many thanks!

---

