---
title: "Firefox problem"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by sakibmoon on 2011-10-08
I am using Ubuntu 10.10 with Windows 7 and the firefox 3.6.23( in both ). I guess for Ubuntu 10.10, this is the latest version.

I am facing problem with Facebook on firefox. The problem is only with Facebook. When I open facebook, it hang after a while. Sometimes, firefox responds again, but only for a short time. I also get a warning of "running script" sometimes. This problem occurs for both platform.

So, what should I do? Should I roll back to earlier version of Firefox? If so, how can I roll-back in Ubuntu?

---

### Post by Krytarik on 2011-10-08
> **sakibmoon said:**
> Should I roll back to earlier version of Firefox?
Even *downgrade*!? :P I'd rather *upgrade*, to version 7 ("firefox-stable" PPA).
See this guide how to do that:

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

If that doesn't solve the issue, check if one or more of your installed add-ons might be the culprit, specifically Adblock Plus, if you are using that (if so, try fine-tuning your subscriptions first, and if that doesn't help, whitelist Facebook).

Hope this helps!

---

### Post by Redblade20XX on 2011-10-08
Hmmm... did this recently start and does this happen on certain pages in facebook or in general after a certain period in time? Might be the pages you're viewing have too much flash or java script on em.  :)

-Red

---

### Post by Krytarik on 2011-10-08
> **Redblade20XX said:**
> Hmmm... did this recently start and does this happen on certain pages in facebook or in general after a certain period in time? Might be the pages you're viewing have too much flash or java script on em.
This ;-) :
> **sakibmoon said:**
> The problem is only with Facebook.
And yes, this is a common issue between Firefox, the scripts on Facebook, and apparently at least Adblock Plus.

---

### Post by sakibmoon on 2011-10-09
The problem is not with the add-ons. I don't use adblock plus.
I can't upgrade as Ubuntu 10.10 do not support firefox 7 as far as I know. If I am wrong, let me know. I didn't face any problem earlier. I used the same add-ons I use now. My friends are using this version in their Windows and they don't face any problem. But on my machine, this happens for both of the platform. Isn't it weird?

---

### Post by sakibmoon on 2011-10-09
> **Redblade20XX said:**
> Hmmm... did this recently start and does this happen on certain pages in facebook or in general after a certain period in time? Might be the pages you're viewing have too much flash or java script on em.  :)

-Red
It has started for a few days. After my current dualboot installation.
It happens on every facebook page. After I log in, the problem starts.

---

### Post by Frogs Hair on 2011-10-09
Try this and see if updating makes a difference .[http://www.liberiangeek.net/2011/09/install-firefox-7-in-ubuntu-10-1010-04/](http://www.liberiangeek.net/2011/09/install-firefox-7-in-ubuntu-10-1010-04/)

---

### Post by Krytarik on 2011-10-09
> **sakibmoon said:**
> I can't upgrade as Ubuntu 10.10 do not support firefox 7 as far as I know.
You should really have a look at the guide I linked to in my first reply, or at those *Frogs Hair* just linked to, for that matter, as both include infos and instructions on how to upgrade through the "firefox-stable" PPA.

---

### Post by VanR on 2011-10-09
> **sakibmoon said:**
> The problem is not with the add-ons. I don't use adblock plus.
I can't upgrade as Ubuntu 10.10 do not support firefox 7 as far as I know. If I am wrong, let me know. I didn't face any problem earlier. I used the same add-ons I use now. My friends are using this version in their Windows and they don't face any problem. But on my machine, this happens for both of the platform. Isn't it weird?


10.10 will run FF7 just fine. At least for me it does.

---

### Post by ?#Yhf%*&amp; on 2011-10-09
Firefox 7 is not available in the Ubuntu 10.10 repositories, but can be installed with an alternate PPA. Open a Terminal window and type all three commands:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```

You will be required to type your password.

---

### Post by sakibmoon on 2011-10-11
I have upgraded Firefox and the problem is solved too.
Thanks a lot to all of you.

---

### Post by blortuga on 2012-08-28
I am having this problem:
Firefox 14, on Precise - 64-bit.

It initially works, and often, will work for an extended period - even several hours.  Then, on a given refresh, it will be "connecting" forever. And the whole browser - all of my tabs, just kind of sits there waiting for some stupid hidden FB element to finish loading.

It SEEMS to have begun AFTER I set up a host-blocking host file. However, I put my old host file back, and the problem continued.  The other change that happened around that time was when Firefox upgraded from 13.x to 14.x.  

Yes, I am using AdBlock.  This is the whole reason why I even use Firefox.

HOWEVER: This ONLY happens on Ubuntu. It does not happen on Windows (7), or Mac OS (10.4.11, 10.6, 10.8).  

If a URL or frame or element is blocked, the browser shouldn't just go off into the weeds. It should 404 that element.  It's bogus to behave like this when elements are blocked by adblock. (if that is even the case).    
(I am also using noscript, but facebook is whitelisted in NS. I am using Flashblock too - but flash is NOT whitelisted. Flashblock is becoming less and less useful, because I have had to whitelist so many sites just to get them to nominally work - and it doesn't block html5-based videos from automatically playing)

  Another measure I took that SEEMED to help, was when I compressed my profile (sqllite database) - but the problem did come back. I think it was a placebo-fix.
Anyway - this is really kind of annoying.  I would be pursuing this with Mozilla, but it doesn't happen on Windows or MacOS.

---

