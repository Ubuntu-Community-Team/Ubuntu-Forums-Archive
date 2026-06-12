---
title: "Can't load the shoutcast webpage in ubuntu"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by sssuizaaa on 2011-11-12
Good morning everyone,

When I try to get to the shoutcast webpage. [www.shoutcast.com](www.shoutcast.com) Chromium gives me this message: Oops! Google Chrome could not connect to [www.shoutcast.com](www.shoutcast.com). Firefox can't connect either: The server at [www.shoutcast.com](www.shoutcast.com) is taking too long to respond.
It does not seem to be a problem with internet or the router as I can load other pages. I can also load the shoutcast page from the same computer but from Windows.
I have been testing several programs and plugins to listen to internet radio and I have ended up with several plugins in Chromium and Firefox but I can't access the shoutcast webpage even after disabling them. I remember accessing the webpage before I started testing media players and so but I can't now.

Any idea about what could be happening?

Thank you

sssuizaaa

---

### Post by Tamlynmac on 2011-11-12
It may be due to SSL security protocols. Try opening [this]("http://www.zerx.com/") search engine and typing [www.shoutcast.com](www.shoutcast.com) into the url bar. I've noticed a number of search engines are now using SSL for security for "increased in privacy".

Hope this helps.

---

### Post by sssuizaaa on 2011-11-13
Thank you Tamlynmac.

I finally found what happened. I edited the /etc/hosts file and at the end of the file there was a line with the [www.shoutcast.com](www.shoutcast.com) url so that was blocking that url.

How that line ended up in that file, who knows.

Regards,

sssuizaaa

---

