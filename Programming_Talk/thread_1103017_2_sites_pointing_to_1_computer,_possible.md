---
title: "2 sites pointing to 1 computer, possible?"
date: 2009-03-22
forum: Programming Talk
---

### Post by cl333r on 2009-03-22
Hi folks
say I have 2 sites: [www.site1.com](www.site1.com) and [www.site2.com](www.site2.com) and want both of them to be on one computer. AFAIK typically they have to point to 2 different computers with 2 different IPs, so is my wish possible?
A link to where I can read about it would be much appreciated.

ps: If it matters: both sites have different content, both written in Java (JSP/JSF) and can run if needed on top of one software-server (like Glassfish).

pps: I have to clarify that I want that from [www.site1.com](www.site1.com) the user be taken directly to the 1st site (which is say on localhost/site1) and from [www.site2.com](www.site2.com) to 2nd site (localhost/site2 accordingly) without asking the user which site he wants to go to.

---

### Post by the_unforgiven on 2009-03-22
Yes - the method is called [Virtual hosting]("http://en.wikipedia.org/wiki/Virtual_hosting")...

---

### Post by cl333r on 2009-03-22
Thanks a lot! I'm looking into it, virtually gonna report back if un/successful!

EDIT: OMG it's obvious and easier than I thought! Wikipedia even uses the same site names as examples: [www.site1.com](www.site1.com) and [www.site2.com](www.site2.com)
It turns out my case is called "Name-based virtual hosting" I just have to check for the browser's "host" header (as specified by the http 1.1 protocol) and redirect accordingly.

---

