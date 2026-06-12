---
title: "Adobe flash player update doesn't work at all!"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by Ben_222 on 2012-03-31
What do I do?I went through some other posts in MultiMedia category,but I do not understand how to DO what they say.I have Ubuntu 10.04 LTS.The older version of flash worked great,but when I updated last Thursday, flashplayer does not ever work. I have an older pc with single core processor,and I watch videos and play QuakeLive on Ubuntu,and use this pc a LOT more than my Windows XP pc.Linux is just so much faster.Seems that not too many people are having this problem.Isnt there a way to install the older version?I did download it, but I have no idea how to install it,or to "replace" some files in the newer version,as some suggested.

---

### Post by santosh83 on 2012-03-31
> **Ben_222 said:**
> What do I do?I went through some other posts in MultiMedia category,but I do not understand how to DO what they say.I have Ubuntu 10.04 LTS.The older version of flash worked great,but when I updated last Thursday, flashplayer does not ever work. I have an older pc with single core processor,and I watch videos and play QuakeLive on Ubuntu,and use this pc a LOT more than my Windows XP pc.Linux is just so much faster.Seems that not too many people are having this problem.Isnt there a way to install the older version?I did download it, but I have no idea how to install it,or to "replace" some files in the newer version,as some suggested.

Hi,

Before you rollback to an older version of Flash Player, did you try reinstalling the latest version again? Perhaps there was a problem during your previous installation process?

Instead of installing from
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
where you only get the tar.gz version of the package, which you must manually extract and install, go to
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
and in 'select an operating system' dropdown menu, choose 'Linux 32/64 bit' (as your case may be), and in 'select a version' menu, choose 'Flash Player 11 for Ubuntu apt.'

If you've got Ubuntu Firefox Modifications plugin installed in your Firefox, you should be able to directly install from the browser by simply clicking OK on the 'Launch Application' dialog that pops up, and following the further prompts.

After installing, and restarting Firefox, type 'about:plugins' in the URL bar, and compare the version of Flash Player plugin Firefox reports as using, with the version Adobe detects through
[http://www.adobe.com/software/flash/about/]("https://www.adobe.com/software/flash/about/")

If it still doesn't work, then try reverting back to the version that's included in this page:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

---

### Post by winh8r on 2012-03-31
Or click on the link in my sig below entitled "Help With Flash" and install and run FlashAid wizard and this will select the optimium set up for your particular system.

Hope this helps.

---

### Post by Ben_222 on 2012-03-31
Hi, I tried both of the above posts,but to no avail.Shockwave flash comes up in FireFox as an addon,but not FlashPlayer.If I go to Manage Content Plugins in Firefox tools,Shockwave Flash and Futurespash show up.I always thought Shockwave was for a different Adobe content.So is Flashplayer installled, or is it just not loading in Firefox? Last thing I tried was using FlashAid.   If I go to Ubuntu software center,the Adobe Flash plugin shows up with a checkmark, so installed.    still confused,....thanks so far for the help....

---

### Post by sdowney717 on 2012-03-31
try installing Chrome the real one.
[https://www.google.com/chrome](https://www.google.com/chrome)

---

### Post by sdowney717 on 2012-03-31
Adobe is dropping support for flash on linux, I think only chrome will continue to have a working flash player.

[http://9to5google.com/2012/02/22/pepper-based-flash-player-coming-to-chrome-later-this-year-adobe-dropping-standalone-plug-in-download-on-linux/](http://9to5google.com/2012/02/22/pepper-based-flash-player-coming-to-chrome-later-this-year-adobe-dropping-standalone-plug-in-download-on-linux/)

---

### Post by lovinglinux on 2012-03-31
> **sdowney717 said:**
> Adobe is dropping support for flash on linux, I think only chrome will continue to have a working flash player.

[http://9to5google.com/2012/02/22/pepper-based-flash-player-coming-to-chrome-later-this-year-adobe-dropping-standalone-plug-in-download-on-linux/](http://9to5google.com/2012/02/22/pepper-based-flash-player-coming-to-chrome-later-this-year-adobe-dropping-standalone-plug-in-download-on-linux/)

Yes, Adobre already dropped support for Linux and gave it to Google, which will implement flash via the new Pepper API. The problem is that both Mozilla and Opera thinks Pepper and Native Client are bad solutions because may reasons and won't implement them.

More info [http://ubuntuforums.org/showthread.php?t=1949908](http://ubuntuforums.org/showthread.php?t=1949908)

> **sdowney717 said:**
> try installing Chrome the real one.
[https://www.google.com/chrome](https://www.google.com/chrome)

Keep in mind that the 64bit version of Chrome doesn't come with a bundled version of flash and will suffer the same symptoms.

Besides, the new Pepper implementation is not ready yet, so Chrome 64bit is still using the same flash installed on your system. The 32bit uses the one bundled with it.

---

### Post by Ben_222 on 2012-04-02
Thanks,   I installed Google Chrome, and flash works on it.Now I will also be hesitant to do any future updates of Flash.....but it was said that Google now does the support..Thanks all for the support!   Oh, does this mean that everyone running Linux and using Firefox won't be able to use the updated Flash?

---

### Post by santosh83 on 2012-04-02
> **Ben_222 said:**
>   Oh, does this mean that everyone running Linux and using Firefox won't be able to use the updated Flash?

I suppose so, but it's not a serious concern. I hardly ever find an essential need to use Flash. Youtube supplies most videos in HTML5 (WebM), and I don't play Flash games. Overall Flash use will also slowly decline I expect, as HTML5 adoption picks up speed, and also now that Mozilla have given-in and agreed to implement H.264 decoding in Firefox.

---

### Post by lovinglinux on 2012-04-02
> **santosh83 said:**
> I suppose so, but it's not a serious concern. I hardly ever find an essential need to use Flash. Youtube supplies most videos in HTML5 (WebM), and I don't play Flash games. Overall Flash use will also slowly decline I expect, as HTML5 adoption picks up speed, and also now that Mozilla have given-in and agreed to implement H.264 decoding in Firefox.

Firefox and Opera users will be able to play flash as long as version 11.2 doesn't break, because it won't be fixed if it does. Perhaps other less known browsers will see an opportunity with this situation and implement Pepper. Who knows?

Is not a serious concern for you, but unfortunately, it is for me. I still depend on flash for many things, including video streaming services I pay for, since I don't own a TV anymore. 

Flash will slowly fade away in the video and game arena, but there are many different things that runs with Flash besides videos and games. For instance, I use LogMeIn, a remote desktop service that you probably know. The interface is flash based. Another service that I like but I'm afraid to fully adopt is bookmark sharing service Peraltrees. Also flash based. There are also many web sites that implement flash uploaders and other stuff.

Even in the video streaming business, it will take some time until HTML5 can provide the same solutions and become financially advantageous to switch. For instance, I subscribe to [globotv](http://globotv.globo.com/) and it is completely flash based. I wonder if they will ever change.

Anyway, I don't like the idea of being forced to use Chrome, but I refuse to use it as primary browser. If I have to use it to play flash, I will use Firefox or Opera as launchers. Firefox has the "Open With" extension and has this functionality built-in.

@Ben_222 please mark the thread as SOLVED if you are satisfied with the solution.

---

