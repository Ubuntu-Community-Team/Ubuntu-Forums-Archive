---
title: "Watching YouTube in Chrome problems"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by ianb72 on 2014-02-21
Hi
Is anyone else having any problems watching YouTube video's in Google Chrome?

Mine will not load any video, I sometimes just get a snowy picture but it will play in FireFox!!

Any Ideas??

---

### Post by deadflowr on 2014-02-21
Since you watch youtube well with firefox, I take it you have flash install system wide.
If so, have you tried disabling the pepperflash plugin in chrome and see how normal linux flash runs?
If you open a tab in chrome and type in the url
```
chrome://plugins
```
you should get the chrome plugin page.
Go down to shockwave flash part and disable the version that isn't 11.2.
(It'll actually say enable?)
Then load a youtube page and see how it plays.

Unfortunately, this will only work for a little while longer, as chrome is dropping the ability to run plugins like that in the near future.
So soon we will be stuck with only pepperflash, which IMO is quite unfortunate.

---

### Post by monkeybrain20122 on 2014-02-21
No problem with pepper flash or system flash. I think in this kind of threads it is always good to be more specific whether you have a Youtube problem or a flash problem. flash != Youtube. If it is just a Youtube problem maybe you should clean your cookies and history then restart chrome.

BTW, most Youtube videos now play in html5 and in chrome it is the default if both flash and html5 are available. It actually took me a while to find one that only plays in flash to test this.

---

### Post by ianb72 on 2014-02-21
> **deadflowr said:**
> Since you watch youtube well with firefox, I take it you have flash install system wide.
If so, have you tried disabling the pepperflash plugin in chrome and see how normal linux flash runs?
If you open a tab in chrome and type in the url
```
chrome://plugins
```
you should get the chrome plugin page.
Go down to shockwave flash part and disable the version that isn't 11.2.
(It'll actually say enable?)
Then load a youtube page and see how it plays.

Unfortunately, this will only work for a little while longer, as chrome is dropping the ability to run plugins like that in the near future.
So soon we will be stuck with only pepperflash, which IMO is quite unfortunate.


I did that and the only version of flash I had was this

Adobe Flash Player - Version: 11.2 r202
Shockwave Flash 11.2 r202

It was working fine a few weeks ago!

All I am getting is the loading circles going round and round!

---

### Post by deadflowr on 2014-02-21
> **ianb72 said:**
> I did that and the only version of flash I had was this

Adobe Flash Player - Version: 11.2 r202
Shockwave Flash 11.2 r202

It was working fine a few weeks ago!

All I am getting is the loading circles going round and round!

Then you're not running chrome, but chromium.

---

### Post by NilPointer on 2014-02-21
I had similar problem watching youtube videos in chromium. Installing chromium-codecs-ffmpeg-extra package solved problem for me.

---

### Post by heldal2 on 2014-02-21
I've got the same problem with Chrome since the last update of chrome to 33.0.1750.117.  Chromium 32.0.1700.107 and  Firefox 27.0.1 works

---

