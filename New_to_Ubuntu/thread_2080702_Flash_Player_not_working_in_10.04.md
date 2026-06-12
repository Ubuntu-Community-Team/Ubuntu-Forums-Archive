---
title: "Flash Player not working in 10.04"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by superkenn on 2012-11-04
I've been running Ubuntu 10.04 for about three years now. Things were fine with it for a long time.

I did some updates after months of not doing them, and it stopped flash from working right after that. I use Firefox and Chrome. Same problem in both.

I've tried reinstalling 10.04 and not doing ANY updates. No luck. I've reinstalled it and done ALL the updates. No luck. I've tried the new 12.04, but had the same problem.

I've tried the Flash Aid for Firefox. No luck.

I've tried these things:
sudo apt-get update
sudo apt-get install flashplugin-installer
sudo apt-get install ubuntu-restricted-extras

No luck.

My hardware is about 7 years or older now. Am I just out of luck? This is becoming REALLY frustrating. Some Flash content plays, and some doesn't. I really don't want to go back to Windows.

Any help would be very much appreciated.

Thanks.

---

### Post by squakie on 2012-11-05
What type of internet connection do your have - wired ethernet to broadband, wireless to broadband router, DSL or dialup?

I know from past experience I had very similar problems until we dumped DSL and went to the faster cable broadband.  The DSL speed was low enough that the request in the web page coding to load/run flash times out before it can run on some (or in my case, it was most) flash videos I wanted to watch.  I got everything from bad performance to errors from flash with no video, to errors from flash saying it can't find the video while it the mean time the video played in the background.

---

### Post by cwsnyder on 2012-11-05
Are you using Google Chrome, or Chromium?

Adobe stopped supporting Flash on the Linux platform, so if the problem reported is that your Flash is not up to date, the problem was not with a program update.

The _only_ Linux supported browser to support the absolute latest version of Flash is Google's Chrome browser for Linux which has its own version of Flash embedded in the browser.

---

### Post by Pilot6 on 2012-11-05
I answered this question at least 4 times. If you have an old cpu, you need to install version 10.3 of flash manually. You will find how to do it, if search the forum.

---

### Post by IWantFroyo on 2012-11-05
Download Google Chrome, and install it with:

```
sudo dpkg -i *packagename*
```

If your flash version is old, this will fix it.

---

### Post by superkenn on 2012-11-05
I'm using broadband. Worked for a long time, then didn't.

I use Firefox, and Chrome. Same problem. I have tried Chromium too. Didn't work.

Manually install Flash 10.3?

---

### Post by superkenn on 2012-11-05
Help me Obi Wans...you're my only hopes...

Nothing working...

I can't find the procedure on how to manually install the old version.

Help a brutha out! :-)

---

### Post by superkenn on 2012-11-08
Can anyone walk me through installing the old version of Flash, please? PLEASE?

---

### Post by superkenn on 2012-11-30
> **Pilot6 said:**
> I answered this question at least 4 times. If you have an old cpu, you need to install version 10.3 of flash manually. You will find how to do it, if search the forum.
Pilot6 can you please post the instructions for manually installing Adobe Flash 10.3 in Ubuntu? I've searched the forum but can't find it. 

Thank you so much.

---

