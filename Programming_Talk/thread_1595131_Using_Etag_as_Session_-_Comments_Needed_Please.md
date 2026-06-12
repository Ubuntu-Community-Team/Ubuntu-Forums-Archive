---
title: "Using Etag as Session - Comments Needed Please"
date: 2010-10-12
forum: Programming Talk
---

### Post by adeee on 2010-10-12
How about using Etag Header as session id of the user for keeping track of user's activity? (if i do not use PHP's builtin Session System) How about building a login system based on Etag rather than cookies and sessions. 

I have spent a few days researching about it few months ago and i didnt find any thing wrong that could go against this idea. Now i want to actually test this idea, but first want some comments from other experts. 

What do you think about this? Any drawbacks/cache problems/client incompatibility issue/security problem that you know about Etag or about Etag based login system? or that could limit Etag's ability of being used as session identifier. 

This could also help user tracking without using cookies and user will have less control over forgery (ie. cookies can be edited easily but to edit headers you need plugins. etc.). 

Any help and ideas in this regard are appreciated.

---

### Post by DanielWaterworth on 2010-10-13
don't do this, it may work some of the time, but there will be caches that won't play nice with it. Cookies are designed for sessions, why not use the tried and tested route.

---

### Post by r-senior on 2010-10-13
> **adeee said:**
> This could also help user tracking without using cookies and user will have less control over forgery (ie. cookies can be edited easily but to edit headers you need plugins. etc.).
Persistent cookies can be edited very easily but the session cookies used for passing session IDs aren't saved on disk and easy to edit. They can be intercepted by sniffing the network but that's also true of HTTP headers (SSL being the obvious solution). 

Is my understanding incorrect? How would it be easy to edit session cookies?

I don't know about PHP, but in Java web apps, URL rewriting is sometimes used as a backup mechanism for sessions if cookies are disabled in the browser.

---

### Post by DanielWaterworth on 2010-10-13
session cookies are just regular cookies, they can be written to disk in exactly the same way, but usually they won't because they'll be set to expire at the end of the browser session. SSL is the only way I can think of to protect sessions against man-in-the-middle attacks.

It's easy to edit cookies of any description in javascript.

Cookies are just http headers that are echoed based on expire-settings and domain.

Apart from caching, Etags have other problems that prevent them from being suitable for sessionid storage.

They are per document, not per domain.
They can be manipulated in flash and hence using them leaves you exposed to csrf attacks.
They are not covered by the same-origin policy.

---

