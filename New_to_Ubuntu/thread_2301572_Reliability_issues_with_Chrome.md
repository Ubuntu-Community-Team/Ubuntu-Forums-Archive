---
title: "Reliability issues with Chrome"
date: 2015-11-03
forum: New to Ubuntu
---

### Post by adrian74 on 2015-11-03
I have a feeling there's a better place for this, and searching didn't yield anything similar to my issue

So, I'm new to Linux/Ubuntu, well kind of a lie, but this is the first time I'm properly using them. My use before was a 12 year old when my dad decided to play with Mandrake several decades ago.

I'm now using it in line with Selenium to run parallel tests on a web based system we use here, and I will go through exactly what I have after introducing you to my issue. 

My issue is that Google Chrome in Ubuntu 14 seems to hang on load, intermittently. It unfortunately has a really low reproduction rate, looking at maybe 1 fail in every 300 runs? 

I have a few boxes networked together, one is the web-server, one is dual use as the Selenium grid hub and DB server, the last are Selenium grid nodes, these are a bare install with X11, XVFB, Chrome, Chromedriver and Java on them. (Plus the Selenium WD listener)

Randomly (and about once in every 300 instances loaded) Chrome fails to load, the processes pop up, but the actual window fails to display. I know this because I have been using XMing on my Windows machine to narrow it down. I've have narrowed it down to Chrome or Ubuntu by successively removing the layers from my cake of APIs to try and cure this.

A single browser thread wouldn't normally be an issue for us, but accompanying this hang is a timeout of 3 hours (don't ask me why). This holds up the entire test suite until the timeout is reached. We have a workaround (read bodge/kludge/hammer) that kills any chrome instance that has been running for longer than n seconds. Has anyone else seen this intermittent hang? How did you cure it?

Ubuntu 14 and Chrome 45 and recently 46

---

