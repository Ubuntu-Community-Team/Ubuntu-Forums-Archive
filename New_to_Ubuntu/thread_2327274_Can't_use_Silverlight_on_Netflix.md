---
title: "Can't use Silverlight on Netflix"
date: 2016-06-09
forum: New to Ubuntu
---

### Post by mark_lewis3 on 2016-06-09
Hello,

I installed ubuntu-16.04-desktop-i386 on an old laptop and then tried to use Netflix, which didn't work because it required Silverlight.

I followed instructions I found [here]("http://askubuntu.com/questions/605460/how-to-install-microsoft-silverlight-on-mozilla-firefox-browser-in-an-easiest-an") but although everything seemed to install properly, Netflix still prompted for Silverlight

I tried to install Chrome but the install of the version I downloaded [from here]("https://www.google.com/chrome/browser/desktop/index.html?utm_source=google&utm_medium=sem&utm_campaign=1001342%7cChromeWin10%7cFR%7cen%7cHybrid%7cText%7cBKWS~TopKWDS-Phrase&brand=CHBD") 64 bit .deb didn't complete

Any suggestions?


Many thanks,
Mark

---

### Post by Zanden on 2016-06-09
Silverlight does not work with chrome anymore

---

### Post by X-RED_Tech on 2016-06-09
... and there's only 64-bit Chrome since a couple of months ago. You can try Chromium but it probably won't work either due to not having the DRM Google Chrome has.

---

### Post by SeijiSensei on 2016-06-09
If you installed Pipelight into Firefox, then you need to spoof your User-Agent string as well.  I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") with the UA string:
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:41.0) Gecko/20100101 Firefox/41.0
```

---

### Post by mörgæs on 2016-06-09
Are you sure that the processor only supports 32 bit Buntu?

---

### Post by T.J. on 2016-06-09
Hello Mark, and welcome to the forums.  

If your laptop has a 64 bit processor. I recommend that you replace the 32 bit Linux with 64 bit, and then install the 64 bit version of Chrome.

 In order to watch Netflix on 32 bit, you have to use Windows Silverlight or EME.  Silverlight is entirely unsupported in any real sense.  Microsoft patches it for bugs or security, but they have otherwise abandoned it, even on Windows.  It is effectively a dead technology, with even less of a life than Flash. You can get it to work on Linux using Pipelight - but I do not recommend it.  Not only is it a substandard, ugly hack, you are opening yourself up to security holes and unstable behavior. 

Using EME on a 32 bit version of Linux is no better. Google is the only one who provides an EME module for Linux. Firefox has been dragging its feet the issue for** years**,* literally*. When they finally decided recently to use Google's EME module, they did not support it on Linux.

For 32 bit Linux users, that means you either have to use another ugly hack or an outdated version of Chrome, since Google switched to 64 bit.  You're much better off and safer to just make the jump to 64 bit.  It will save you hours of headaches.

---

### Post by SeijiSensei on 2016-06-09
> You can get it to work on Linux using Pipelight - but I do not recommend it. Not only is it a substandard, ugly hack, you are opening yourself up to security holes and unstable behavior. 

What security holes might those be?  Pipelight interacts solely with the WINE implementation stored in ~/.wine-pipelight.  How is some theoretical security issue in Silverlight supposed to propagate into Linux?  Moreover Pipelight works amazingly well and is quite stable.  Is your opinion based on actual testing and usage?  I use Pipelight to run the Windows Flash player as well as Silverlight since Adobe has abandoned Flash for Linux.  Pipelight is a long-standing project that reflects a lot of hard work by its developers whom you just casually slandered.

---

### Post by T.J. on 2016-06-09
Answering that is off-topic and really doesn't help Mark.  My comments here in no way reflect on you either.  It's just my observation, and feel free to ignore it if you wish.

No slander was intended. Slander implies deliberate deception or malice. I have neither.  It is generally considered acceptable and customary for programmers to describe solutions that that go to extensive or even unusual lengths beyond normal specifications as "ugly" or "substandard" and as a "hack."  It has nothing to do with the personal ability or reputations of those involved.   I have created many "ugly hacks" myself, and I am in no way injured or upset to have them described in those terms. It is simply an opinion, rendered in the terms that programmers tend to use.  In any case, you were right to ask for an explanation.  Be assured that no ill was intended.

I actually don't remember if I have used Pipelight. I remember researching it. I may have even tried it. I have my doubts, but I have used similar techniques over the years before virtualization became so easy. That said, there are some realities about Pipelight/WINE that should not be ignored.

Whenever you are running foreign binary code on top of your operating system through a translator, you automatically inherit any defects that software running on the binary interface might have, as well as create a few new ones.  That is a given when using the translation techniques, and has nothing to do with WINE alone.  Now, that doesn't mean that WINE does not close or address some of these issues.  I'm sure they do, but it is not their main focus, and I doubt they are going to spend time to address every Windows bug and security report to verify how that bug will manifest under WINE. Running Windows code on WINE by definition is insecure, that is why you never extend its privileges.  It is usually true that the worst result is corrupted data.

When you use techniques such as Pipelight, you are taking a risk, because it is impossible to predict with complete certainty how stable the binary translation will be in real-time, due to upstream changes by Microsoft. Regardless of how many precautions you take, it may lock up your system or even crash it entirely.  If it were flawless, Pipelight wouldn't publish the FAQ. As for security holes, I never said or suggested that they can "propagate to Linux".  It is theoretically possible they could propagate to Windows machines on your subnet, but who cares right? Other users in your home might, because functional translation may not have the same safeguards as running the code in its native environment.

That doesn't even address another, but perhaps more important issue. Pipelight may violate patents or the Microsoft license agreements.  The codecs are not licensed by their owners to be run on other operating systems in that manner - hence it may be illegal use. That in itself may ban the topic of Pipelight from the Ubuntu forums.
 
My point is why bother with all that work, the unknowns, and the legal problems, when there is an easier, far more reliable, more sane method, especially for a new user like Mark?  

In my opinion, it is one thing to exhibit hacker prowess, but the easiest solution is usually the correct one.

---

