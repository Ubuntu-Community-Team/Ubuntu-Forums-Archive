---
title: "Flash: Windows vs Ubuntu"
date: 2010-08-17
forum: Recurring Discussions
---

### Post by mishfit on 2010-08-17
I originally wanted to title this post, "Flash: Windows vs Ubuntu (the question no one seems to [want to] answer)".

But it looked a little ridiculous (not to mention long).

The question behind the title still stands. I'm not interested in help triaging my hardware or internet connection speeds
(it is a single dedicated commercial ip at 6Mbps down/2Mbps up...I work from home)

Regardless of hardware (crappy or great) Windows appears to be capable of greater streaming flash performance than Ubuntu. I want to know why.

Let's review the "crappy" hardware scenario.

A 10yr old gateway desktop with an upgraded nvidia pci graphics card plays hulu/youtube/runs my test apps to its hearts content on Windows whereas running in Ubuntu 9.04
results in choppy video and dizziness to most onlookers (I'm apparently the only one in my household who doesn't get dizzy...I blame significant stretches at sea in my youth for immunity).
In Windows even the on-board Intel graphics chip handled flash fine...upgrading had little effect in either operating system, counter to what some posts suggested.

The "great" hardware scenario offers little hope.

An AMD64 powered machine with dual sli nvidia cards (and enough other bells and whistle) plays flash fine, in Ubuntu and Windows (hooray!).
But when in Ubuntu and the video is played in full screen...the choppy video comes back. This doesn't happen in Windows XP.

Now I'm not trying to be incendiary with this post. I'm using Ubuntu because it does a whole lot of other things for me much better than Windows
does (or probably ever will). But I read other posts about spotty flash performance and come away with nothing...some suggest that flash is so processor intensive
that the hardware is to blame (really...last time I checked Windows in and of itself is more processor intensive). I like starting a Linux box and seeing
little to no activity, almost as if the machine reports back, "ready and able, sir! Give me your best shot." And in almost all cases it performs better than expected.
Some report a shoddy graphics chip that everyone should dump at their earliest convenience
(what?...Windows can turn any sorry excuse for abstract sand sculpture into passable computer accessories?...hardly).

I understand they have one edge (maybe two)...a strangle hold on most manufacturers and vendors and an influence which drives most hardware companies to extreme lengths of secrecy that ultimately reduces their consumer base.
This alone should not rule flash performance (although if there is more I invite anyone to educate me).

---

### Post by uRock on 2010-08-17
Don't ask us, ask Adobe, the writers of flash.

---

### Post by philinux on 2010-08-17
Moved to recurring Discussions forum.

---

### Post by cchhrriiss121212 on 2010-08-17
Here's the summary AFAIK:
Flash stinks on linux because it does not make use of hardware acceleration, hence the high cpu
Adobe do not write a better plugin with hardware acceleration because linux does not have a stable API
You can watch flash with better performance if you just watch the .flv file in your /tmp folder with totem or something

Anyone feel free to correct this summary, as it is just what I have picked up from these forums.

---

### Post by uRock on 2010-08-17
> **cchhrriiss121212 said:**
> You can watch flash with better performance if you just watch the .flv file in your /tmp folder with totem or something
That is a good idea.:D

---

### Post by Raffles10 on 2010-08-17
I'm posting this from a Windows 7 install, the reason = "flash crashes".

I've been using Linux for the best part of five years, over that time I've tried almost every major distribution from Arch to Zenwalk. One problem I've experienced with many distro's is that playing streaming flash video in a web browser will eventually crash my pc. This always happens without exception, with Firefox or Chromium, the video will play and sooner or later my pc locks up, the whole screen starts to flash slowly and I lose all inputs, no keyboard or mouse, the only option is a hard reboot.

I can only remember this beginning about 18 months to 2 yrs ago. I've tried every nvidia driver from 185.xx to the latest 258.xx. I've tried different ways of installing flash from using the default provided in the repo's to downloading the latest from adobe and installing manually. The flash crashes keep coming.

So then you think it might be a hardware problem, a dying GPU, dodgy RAM or even overheating ?

The one thing that counts against all those is that this has never happened in Windows Vista or Windows 7.

](*,)

---

### Post by mishfit on 2010-08-17
Yes...whenever I'm able I download the flv files. I'm not sure how possible that is with hulu/amazon video on demand...but it works quite well for youtube...still, if the ultimate reason flash doesn't work perfectly is standardization (via a stable api)...then there's hope

---

### Post by cchhrriiss121212 on 2010-08-17
> **uRock said:**
> That is a good idea.:D
A better idea would be firefox add-on that automatically launches flash videos in the default stand alone video player.

---

### Post by gandaran on 2010-08-17
> **uRock said:**
> Don't ask us, ask Adobe, the writers of flash.
sorry but I don't think its an entirely adobe problem, I didn't have the flash full window problem before on Ubuntu 9.04 and 8.04
now on 10.04 many users complain including me.
I have the collection of all released adobe flash-plugins versions and I have tried the same flash version that used to work very well on 9.04, it has the same problem with full window in Ubuntu 10.04! so where is the problem? Ubuntu? firefox? drivers? I don't really know! but I still question why on older Ubuntu versions there was no problem with flash on my computer?

---

### Post by lovinglinux on 2010-08-18
> **cchhrriiss121212 said:**
> Here's the summary AFAIK:
Flash stinks on linux because it does not make use of hardware acceleration, hence the high cpu
Adobe do not write a better plugin with hardware acceleration because linux does not have a stable API
You can watch flash with better performance if you just watch the .flv file in your /tmp folder with totem or something

Anyone feel free to correct this summary, as it is just what I have picked up from these forums.


It does use hardware acceleration. I used to think it doesn't too, but it seems the real problem is that flash can't use XV output and it doesn't play well with Compiz. Read [this]("http://blogs.adobe.com/penguinswf/2008/05/flash_uses_the_gpu.html").

> **cchhrriiss121212 said:**
> A better idea would be firefox add-on that automatically launches flash videos in the default stand alone video player.

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

I'm the developer btw. It doesn't work on all sites, but is a start.

Other alternatives can be found at [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

> **gandaran said:**
> sorry but I don't think its an entirely adobe problem, I didn't have the flash full window problem before on Ubuntu 9.04 and 8.04
now on 10.04 many users complain including me.
I have the collection of all released adobe flash-plugins versions and I have tried the same flash version that used to work very well on 9.04, it has the same problem with full window in Ubuntu 10.04! so where is the problem? Ubuntu? firefox? drivers? I don't really know! but I still question why on older Ubuntu versions there was no problem with flash on my computer?

See [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by cavrep on 2010-08-18
The best thing Apple did was to ban flash which is an unnecessary pain in the butt. If you are downloading Utube use mp4 instead and which has better quality.

---

### Post by mishfit on 2010-08-18
Thank you "lovinglinux", those links are priceless...very informative. They go a long way to answering *why* I get two different experiences on the same hardware in different OSes. They also give great pointers to those able and willing to assist linux surpass Windows in this area.

Thanks

---

### Post by lovinglinux on 2010-08-18
> **mishfit said:**
> Thank you "lovinglinux", those links are priceless...very informative. They go a long way to answering *why* I get two different experiences on the same hardware in different OSes. They also give great pointers to those able and willing to assist linux surpass Windows in this area.

Thanks

You are welcome.

---

### Post by sydbat on 2010-08-18
> **cavrep said:**
> The best thing Apple did was to ban flash which is an unnecessary pain in the butt. If you are downloading Utube use mp4 instead and which has better quality.Steve? Is that you? Hey, how's the new iWhatevers coming along??

---

### Post by cchhrriiss121212 on 2010-08-19
> **lovinglinux said:**
> It does use hardware acceleration. I used to think it doesn't too, but it seems the real problem is that flash can't use XV output and it doesn't play well with Compiz. Read [this]("http://blogs.adobe.com/penguinswf/2008/05/flash_uses_the_gpu.html").

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

I'm the developer btw. It doesn't work on all sites, but is a start.

Other alternatives can be found at [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

Very interesting links, thanks for posting them. I was hoping someone would post an add-on like that, it seems like you have made some good progress on it.

---

### Post by lovinglinux on 2010-08-19
> **cchhrriiss121212 said:**
> Very interesting links, thanks for posting them. I was hoping someone would post an add-on like that, it seems like you have made some good progress on it.

Thanks. I have been working on the extension issues, but I still need to add more sites, which is the most tricky to do.

---

