---
title: "Occasional slow internet speeds and video buffering"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by john339 on 2014-12-26
Hi everyone. I'm a first time poster and recent convert from windows who had only occasionally used ubuntu in the past through wubi. Ubuntu seems to cover all of my needs with open source freeware ,customization opportunities, and lack of advertising, but can still sometimes feel less stable. Occasionally I will experience drops to very low speed; sometimes disconnecting and reconnecting to my wifi will cover it and sometimes it won't. I did enter a small bit of code that was supposed to help internet speed on wifi, though I don't think I'd be able to find that specific code again. Entering code is very new to me and I don't really plan to use ubuntu in a very intensive way. I stream a lot of video, mostly youtube and blip, and get mixed results on both. Often times youtube will be great then suddenly videos will not load or buffer extensively, usually defaulting to the lowest quality. Blip often plays audio fine, usually even without buffering, but mostly shows me a series of stills for video. I'm currently attending a college that blocks torrenting so I have been stockpiling torrents while home for the holidays; recently about 4-5 4-15 gig torrents a day. Will that impact performance? I also rarely turned my computer off as a windows user; is that something I will need to do more often on ubuntu? I liked chrome the best on windows but have been finding firefox faster on ubuntu; will browsers make a difference? My computer is an hp envy x360 if that helps. I appreciate any help I can get.

---

### Post by DuckHook on 2014-12-27
Hi john339 and welcome to Ubuntu and the forums.

To answer your questions in the order they were asked:> **john339 said:**
> ...used ubuntu in the past through wubi.WUBI is no longer offered nor supported. It was a very fragile environment and extremely brittle even when little things went wrong. It was designed to introduce Windows users to Ubuntu and in your case appears to have done its job. Are you still running on WUBI, or are you dual booting, or have you nuked Windows and installed only Ubuntu?

Also, what flavour and version of 'buntu are you using?> ...sometimes feel less stable. Occasionally I will experience drops to very low speed...Are you referring to a drop in CPU or graphics speed, or is it net transmission speed? If your whole computer is slowing down, then it won't only be the browser that is sluggish, but other apps not dependant on network throughput, like LibreOffice. You can see if the CPU is being overtaxed by running *top* in a terminal. Keep it running in a corner while you are going about your business and it will show you CPU load and memory use at all times. There are also ways to see if GPU is overtaxed, but this depends on the GPU chipset and driver you have installed.> ...sometimes disconnecting and reconnecting to my wifi will cover it and sometimes it won't...I stream a lot of video...I have been stockpiling torrents while home for the holidays; recently about 4-5 4-15 gig torrents a day. Will that impact performance?This is a highly likely candidate for the slowdowns you are experiencing, but without further info it is impossible to say for sure. Network issues are not easy to hunt down. The problem could be at the router end, especially if you are torrenting multiple torrents with connections from many peers. Port usage is notoriously heavy on your router with torrenting. In any case, your network loads are extremely heavy and will tax any pipeline. You should carefully note whether your browsing experience improves when you are not torrenting.> I also rarely turned my computer off as a windows user; is that something I will need to do more often on ubuntu?Even less often with Linux, unless you want to&#8213;as in the case of rebooting after kernel updates. There are people who don't turn off their computers for years and make a game of seeing who has the longest uptime. Linux is an extremely stable OS.> ...will browsers make a difference?They do, but not between Chrome vs Firefox. Both are heavy-duty browsers that take up lots of resources. Primitive browsers use very little resources, but new users will not stand for them. They tend to be appreciated by and confined to power users who are paranoid about security.> My computer is an hp envy x360 if that helps.It does, but not as much as one would hope. There's too much variation in the build-types and I'm unfamiliar with the laptop. Please provide as much HW detail as possible.

Utilities to help you find the problem:

Instead of *top*, you may wish to run *htop* which provides a prettier and more graphically intuitive presentation of the processes, memory usage and CPU load on your system. You can run *iftop* to see how much bandwidth your network is using. *iftop* must be run using sudo. Refer to its *man*page for instructions. Be aware that you may have to point it to your wireless interface instead of your wired one. Your wireless interface is probably called *wlan0* but you should check what it is called using:```
iwconfig
```

---

### Post by hakuna_matata on 2014-12-27
> **DuckHook said:**
> WUBI is no longer offered
Versions of wubi.exe are still available:

[http://releases.ubuntu.com/trusty/wubi.exe](http://releases.ubuntu.com/trusty/wubi.exe)
[http://releases.ubuntu.com/utopic/wubi.exe](http://releases.ubuntu.com/utopic/wubi.exe)

But these versions are not easy to use because of known issues:

14.04 and above: [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") workaround: [http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)
14.04.1: [bug 1367071]("http://bugs.launchpad.net/wubi/+bug/1367071") workaround: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)
14.10: [bug 1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") workaround: [http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861](http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861)

So it is better to avoid Wubi.

But IMHO slow internet speeds and video buffering are not typical Wubi issues. Maybe, an issue of the Wifi driver or an issue of some plugins like Flash.

---

### Post by crip720 on 2014-12-27
If trying watch Youtube and torrenting at the same time that might be a problem.  I would stop all downloading and go to speedtest.net  in your browser of choice and find out what your speed is.  Do a few tests at a time and at different times of the day.  Check how the graph goes, it should be nearly flat.  Are you the only one using wifi?  If you have  dynamic IP address, try to change to another one.  Sometimes I get an IP address from my ISP that barely gives me half speed, changing to another I get full speed.  See also what speed your ISP is supposed to be giving you.

---

