---
title: "old laptop revival"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by duruttye on 2008-10-23
Hey!

I have an old laptop, dell latitude PCX (I guess) it has 128 mgram, and a 650 MHz processor. What would be the best solution for it?

My girlfriend wants to use it for SPSS, I tried that on the ubuntu 8.10 version and it seems to be working. Furthermore the laptop has no wireless nor ethernet card. I bought an usb wireless adapter.

So, I need some kind of ubuntu to work whit those specs, to recognize that flash drive and to have wine.

Can I install somehow a barebone ubuntu, or xubuntu, without games or fancy stuff??

If any of you has some ideas, pleas tell me so!

Thanx

---

### Post by neurostu on 2008-10-23
I would try Xubuntu or puppy linux. I'm not sure what the sys reqs are for Xubuntu but I think you're well within them.

---

### Post by halitech on 2008-10-23
even Xubuntu will be slow on that. Personally, stay away from puppy or dsl, not worth the hassle of setting them up. If you want to see that machine work nicely, go for Debian+XFCE and it will work nicely.

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by Duck2006 on 2008-10-23
> **halitech said:**
> even Xubuntu will be slow on that. Personally, stay away from puppy or dsl, not worth the hassle of setting them up. If you want to see that machine work nicely, go for Debian+XFCE and it will work nicely.

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

+1 on puppy, or DSL linux, it would be your best bet.

---

### Post by bodhi.zazen on 2008-10-23
Personally I like Slackware distros on old hardware. Zenwalk or Wolvix come to mind.

You can do Ubuntu, IMO the performance is the dame if you Debian + XFCE or Ubuntu + XFCE. The difference is you install only what you need and not xubuntu-desktop.

See also :

[https://help.ubuntu.com/community/Installation/LowMemorySystem]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)
[URL="http://www.ubuntuforums.org/showthread.php?t=339029"] 
[/URL]

---

### Post by snowpine on 2008-10-23
I have a similar-vintage Dell laptop (the Cpx). It has served me well with several different Linux distros. My recommendation is install some more ram (I think you can fit 512mb in there) and you will have many more options, including Xubuntu and Ubuntu. 128mb is very limiting. I am in the middle of distro-hopping, so I'm not going to recommend any one in particular as my "personal pick" but I will say that there are some good threads here on the Forums about lighter alternatives to Xubuntu, should you decide to go that direction. It is all about your preferences of speed vs. eye candy. Personally, I am all about the speed, so I would not use "regular" Ubuntu on a Pentium-3-era laptop. Your opinion may vary. :)

---

### Post by rockerphil on 2008-10-23
my personal advice is to use either Fluxbuntu. it's technically not supported, but it works well on older hardware. i personally ran it for several months on the desktop i'm now using which has 128 MB of pc133 SD RAM and a 500 MHz Intel Celeron processor. either that or you can do what i did after switching from Fluxbuntu and build the OS from the command line up using this tutorial

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

which runs quite well with the same specs. hope this info helps,

Phil

---

### Post by sleepingdragon on 2008-10-23
You might also want to consider Dream Linux. I've had it run on 128Mb, the performance is actually quite good - beautiful desktop too.

---

### Post by duruttye on 2008-10-23
Thanx guys for all the replies!

Right now, i'm testing xubuntu 8.04, and fortunately i managed to install it without any hassle. The thing is, that i can connect to the wireless router, but i can't ping the modem... so, there is no wireless.

For those who suggested dsl and puppy, do you think that i will be able to run on those something like SPSS statistical application with wine?? And what about the usb wireless card? I red somewhere that for example that the dsl kernel is outdated...
Anyway, any thoughts on that wireless thing?

The usb wireless card is canyon something, the router is level one, the modem is speedtouch 516v6 or something like that.

On my other laptop i cannot test this problem, because it has a built in wireless modem, if I disable the wireless, than the usb adapter is not working...

So, thanx again for the advice and hope to hear from someone about this wireless thing.

---

### Post by duruttye on 2008-10-23
Well never mind that wireless problem, 'cause i plugged in for a few times and now it's working.

The odd thing is that it an also connect to a wired network... no idea where it got that network, there are no cables here :)

Thanx again guys!
ubuntu forum rocks:guitar:

---

### Post by duruttye on 2008-10-23
Here I am again.
The laptop is pretty slow.
I would like to really strip it down.
This is what I really need:
-pidgin
-firefox, or some lightweight browser
-wine
-open office spreadsheet, but only spreadsheet?
-and some music player.

is there any way I can do that?

I'm open to any suggestions that will make this old fighter a little faster :)

Thank you!

---

### Post by duruttye on 2008-11-02
just to keep you updated:)

installed just a command line  system with an alternate cd, then I installed only what I wanted: fluxbox, xorg, xterm, wdm, menu and opera
I even managed to make my wireless usb adapter to work, from the command line, that's an achievement for me!!! Althought I cannot make it permanent, I have to configure it every time... but I'm happy with  it :)

for statistics I will probably use R and gnumetric, so ther will be no need for wine.

so far, the laptop performs pretty good, no complains!

Hope this will help someone!

---

### Post by neurostu on 2008-11-04
If you get sick of re-configuring the wireless everytime you boot you should create a shell script to do it for you...

---

### Post by o.besner on 2008-11-04
I guess I might be too late, but if you ever get tired of Xubuntu, give Arch Linux a try. Very versatile, easy to install (basically just follow their wiki), badass package manager, and it's a rolling distro (Which means you don't need to upgrade from one version to the other like Ubuntu - which can really ruin your day). There is no fixed GUI, so you could go for XFCE or Fluxbox, or even have both.

---

