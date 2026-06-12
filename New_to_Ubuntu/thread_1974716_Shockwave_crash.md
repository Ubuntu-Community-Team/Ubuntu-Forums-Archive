---
title: "Shockwave crash"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by meduser on 2012-05-06
Since the new release almost 2 weeks ago, I get shockwave crashing all the time. It is happening in Chrome, Chromium, and Firefox.

I am running 12.04 LTS, 32 bit. I have a Phenom 4 black chip, and 12 gigs of ram. The hardware is not the issue, as Windows(the pc is a dual boot) runs shockwave flash with no issues.


Any help is greatly appreciated.

Thanks,
Med

---

### Post by gordintoronto on 2012-05-06
I would run 64-but with that much RAM. Can you give an example of a site that crashes?

---

### Post by meduser on 2012-05-06
I tried the 64 bit, and was having issues freezing all over the place, so I wiped the pc and started over.

I didn't think about it limiting my ram size :(

Yahoo videos freeze. When you click on a story, and it has a video with it, it will freeze. Same with youtube. 

I have tried to watch videos over at TSN and ESPN and they both end up stopping part way through, then the jigsaw puzzle piece shows up, then the crash message.

I am sure it is flash player, as I have seen tonnes of posts about blue faces in posts since the update.

---

### Post by meduser on 2012-05-06
well now chrome is freezing on every yahoo page...


I love Ununtu, but I have been having nothing but problems with 12.04 since it was released....

---

### Post by gordintoronto on 2012-05-06
Did you upgrade or clean install? What video card? I think you are having problems with Flash, not Shockwave. Did you install the Restricted Extras?

---

### Post by meduser on 2012-05-06
I installed a clean install. I have a geforce 9600...not up to snuff for todays standards, but was a hell of a card 3 years ago)...still, it is dual monitors, and way faster than the onboard video card. 
Here's a link to the card:
[http://www.geforce.com/hardware/desktop-gpus/geforce-9600-gt](http://www.geforce.com/hardware/desktop-gpus/geforce-9600-gt)

I have been having issues with flash since 12.04 was released.

My pc is fast, but not overclocked, as for what I do, it is not required.

---

### Post by meduser on 2012-05-06
> **gordintoronto said:**
> Did you upgrade or clean install?  Did you install the Restricted Extras?

Clean install, downloaded directly from the Ubuntu web site, not a mirror. 

Yes, I have the restricted extras installed. Watched a movie last night on my pc.

---

### Post by meduser on 2012-05-06
it would also appear to be more chome/ chromium based, as the same pages are not crashing in firefox right now.

---

### Post by Curtis6767 on 2012-05-06
Have you tried Flash Aid? 

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by meduser on 2012-05-06
I have heard of it, I downloaded it, but I do not know how to make it work with Chrome/ Chromium

---

### Post by Curtis6767 on 2012-05-06
Flash Aid is for Firefox. It's supposed to make sure you have the most up to date version of Flash by removing older versions.

---

### Post by meduser on 2012-05-06
Yeah I know what it does. From what I have read it makes sure there is no conflicting or duplicated flash versions running. I also know it is for firefox, but it is supposed to work for chrome also.

---

### Post by meduser on 2012-05-07
I have flashaid installed on Firefox now and there is no difference..continues to crash

The error shown says: The following plug-in has crashed: Shockwave Flash

---

### Post by Curtis6767 on 2012-05-07
Unfortunately, if you google your issue with Flash, you will find that this has been a problem for Ubuntu going back several generations.

Canonical must be aware of this problem so hopefully they'll offer up a fix sometime soon.


GL

---

### Post by meduser on 2012-05-07
I have seen a bug for this...is there anyway to fix it, as I can't access most of what I come to the web for. To watch the news, watch sport highlights, etc.

---

### Post by meduser on 2012-05-07
I have googled it, and all I seem to find is that it is a bug, but there is no fix offered. I have been on Linux since September 2011, and this is the first reall issues that I have with flash

---

### Post by Curtis6767 on 2012-05-07
Try looking through this thread: [http://ubuntuforums.org/showthread.php?t=1968155](http://ubuntuforums.org/showthread.php?t=1968155)

There's a post about Flash on the front page.

---

### Post by meduser on 2012-05-07
thank you ..checking it out now.

---

### Post by meduser on 2012-05-07
Hi, I had already read that post and tried the flash fix listed, Still the same issue.

Isn't there some kind of terminal commands to see what is going on and why the crash happens?

---

### Post by meduser on 2012-05-07
still searching

---

### Post by meduser on 2012-05-07
so what changed to make flash so flaky? I have never had issues with flash and the such like this.

---

### Post by deadflowr on 2012-05-07
I think your flash problems might be more related to your graphics card than flash. Their have been several reported bugs concerning the latest nvidia drivers, mostly doing with compiz, but I suspect they might also be messing with your cards use of flash.

 I personally have no problems running flash in either 32-bit or 62-bit with open-source ati drivers. In firefox or chrome.

---

### Post by meduser on 2012-05-07
I have already downgraded my drivers for the card.....

my virtualbox, running OSX Snow Leapard does not have any issues..lol

---

### Post by meduser on 2012-05-07
So I would venture to guess that it is a conflict between Ubuntu and flash, as OSX and Windows 7 do not have the same issues.

---

### Post by gordintoronto on 2012-05-07
It might also be Compiz.

I have a 9400 GT card, Youtube, TSN and Yahoo work perfectly in 12.04 64-bit, installed on a USB flash drive.

---

### Post by deadflowr on 2012-05-07
If you feel the need to report a bug, do so.
Here's a link if you don't know how.

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")


Ironically, the best tutorial for bug reporting I have found is an ubuntudevelopers youtube video.

---

### Post by Curtis6767 on 2012-05-08
**Warning:** The following link is posted for educational purposes only. Following any of the mentioned procedures could trash your system rendering it useless and beyond repair.  Think twice before initiating any of these so-called fixes.

The information on this site, which is new to me, is two years old, but there might be something a value within. The front page is aimed at 64bit users, but there is a section for 32bit users, as well. I imagine by now that you've probably seen this site or found similar tips on another site but in case you haven't, then here you go:

[https://ubuntugenius.wordpress.com/2010/06/04/how-to-fix-firefox-vs-adobe-flash-problems-in-64-bit-ubuntu/](https://ubuntugenius.wordpress.com/2010/06/04/how-to-fix-firefox-vs-adobe-flash-problems-in-64-bit-ubuntu/)


 GL

---

### Post by meduser on 2012-05-08
Thank you so much for all your help. 

I don't think it is a bug, as others would be having the issue, I just can't figure out what the issue is.

does jdk7 have anything to do with flash? I tried to install java, but got an error that it couldn't be installed.

I'll check the link out now.

---

### Post by meduser on 2012-05-08
This is the error with JDK 7


sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer


Thinking this is more the error than anything

---

### Post by meduser on 2012-05-08
so I ran:


sudo rm oracle-java7-installer*

ran update, ran apt-get upgrade, no errors. I opened up you tube and the video is working...no crashing..

I think I got it.

---

### Post by Curtis6767 on 2012-05-08
I installed IcedTea Plugin. Notice on the image that JDK7 is not installed. The Software Center made that decision, not me.

I have had no problems with Java sites.

---

### Post by meduser on 2012-05-08
well, I have been running a video for 20 minutes now, with geany open as I am editing some websites I work on.

Not one freeze or crash.

I am going to say it is the JDK -7 that did not install, and caused issues with flash.

It appears to be fixed.

---

### Post by meduser on 2012-05-08
I was wrong...just crashed 2x in the last 5 minutes on yahoo watching the story about a guy who fell into a vat of acid.

---

### Post by meduser on 2012-05-10
so am I the only one having this issue?
I can't watch more than 20 secs of a video before it crashes.

Oh, and when it is playing, I am now getting the blue faces happening.

---

### Post by gordintoronto on 2012-05-11
Blue, maybe I can help with:
[http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

Flash works great for me.

---

### Post by meduser on 2012-05-11
Thank you so much. the blue is gone, and I just watched a hockey highlight package and no crash...

fingers crossed.

Thank you.

---

### Post by meduser on 2012-05-12
no..still had blue faces, and shockwave flash keeps crashing.

I am also getting saying unresponsive page...

---

### Post by meduser on 2012-05-15
so how do I troubleshoot this?

---

### Post by Zzl1xndd on 2012-05-15
I was having a similar issue still not fully resolved but switching over to Unity 2d at the log in screen has fixed it for 98% of the sites I go to.

---

### Post by meduser on 2012-05-19
shouldn't have to disable unity to watch videos....

I am stunned that I am the only one who is having this issue

---

### Post by anewguy on 2012-05-19
I've been fighting that with flash for a LONG time.  I've tried unity 2d, gnome shell with no effects, chrome, flashaid, etc., etc., etc. - with no fix.  I've tried gnash and lightspark (?) and all that happened was lightspark saying it didn't support the current video format.  I haven't been able to watch most videos in a couple of years.  Adobe is moving away from supporting Linux from what I hear, so there will be no patches from them either.  What's really crazy is that I can go to shockwave (you know, the guys who originally did flash) and try something like the daily jigsaw, and the advertisement video (that requires flash) plays fine there before it loads and uses shockwave player for the game.

Good luck - I don't see much hope in this unless either the open-source projects can catch up or if Adobe releases the linux version as open-source.

---

### Post by meduser on 2012-05-19
I hate to wine about it, as the Ubuntu system is great to be on, but if I can't watch videos it seems pointless to keep this as my operating system. I have never had an issue with flash crashing until 12.04, and I am on my third Ubuntu release..11.04 and 11.10 were fine for me and videos.....I just don't get why they wouldn't be keeping up with things, as videos play on almost every website I go to. Sometimes it is the ads, other times it is a story....but to not be able to play something is very frustrating.

---

### Post by meduser on 2012-05-19
So this is kind of weird...I had cairo dock installed, but was not using that as it seemed to be too much going on....I just purged it from system, as I didn't like it, and now I can't seem to make flash crash....I have watched 17 straight you tube videos, and 5 different stories from yahoo news, and no issue...
before removing cairo dock, I would freeze before the video was loaded, or the whole screen would just freeze.

I sure hope this was the problem, as I am very sick of opening a page, and it crashing within seconds.

---

### Post by meduser on 2012-05-19
2 hours later and still no crash...I think I found the culprit...lol

---

### Post by anewguy on 2012-05-20
Must be nice - I still can't watch most flash items.

---

### Post by meduser on 2012-05-20
Not so quick...back to errors, crashing and freezing....this sucks.

---

### Post by idoitprone on 2012-05-20
> **meduser said:**
> Not so quick...back to errors, crashing and freezing....this sucks.

then open your browser in the terminal

like this

```
firefox 2>&1 | tee -a firefoxLog.txt
```

paste firefoxLog.txt so we can know what is going on. You can watch the terminal screen shooting out random errors if you wish.

This is probably faster to diagonise your errors

---

