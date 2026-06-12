---
title: "Please fix the boot issue to make it completely graphical"
date: 2011-07-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rausuar on 2011-07-10
I will be happy when the Ubuntu developers pay real attention and fix the startup and shutdown process of ubuntu to make it completely graphical, no TTY text please!

Ahh! and I know that some people say that they like text to appear as they can be aware of problems, but then, you can fix the issue and again if you want to boot with text add an option or check the logs!!!

---

### Post by cariboo on 2011-07-10
Don't use the proprietary drivers. Plymouth works well on my nvidia system when using the nouveau driver, and the default Intel driver on my netbook. I plan on installing Lubuntu on an older HP laptop soon, so I'll see how the open source ATI/AMD drivers work.

---

### Post by Harry33 on 2011-07-10
> **cariboo907 said:**
> Don't use the proprietary drivers. Plymouth works well on my nvidia system when using the nouveau driver, and the default Intel driver on my netbook. I plan on installing Lubuntu on an older HP laptop soon, so I'll see how the open source ATI/AMD drivers work.

I have one 64-bit ATI (HD 3200 Pro) installation with xserver-xorg-video-ati driver.
This is Natty Narwhal.
However, the booting process is not ful.y graphical.
Plymouth appears, then disappears (black screen), then Plymouth reappears and changes smoothly into gdm.

---

### Post by MacUntu on 2011-07-10
I haven't seen a fully graphical _shutdown_ in years. :(

---

### Post by teachop on 2011-07-10
> **MacUntu said:**
> I haven't seen a fully graphical _shutdown_ in years. :(
The only times I have seen Plymouth 100% work (in prior releases, can't get 11.10 to boot at all) were live CD boots.  Sometimes.

---

### Post by jerrylamos on 2011-07-10
S - L - O - W - !  In case you haven't noticed, Graphical takes a lot more code and very much more processor cycles.  I prefer fast boot & shutdown since as a tester I'm forever booting & rebooting.

Xorg is also problematical many times - it's still crashing here - so "graphical xorg" is more likely to fail on early development.

Yeah, the text is ugly, sometimes it has some very useful info when things are going crash.

Having said that I usually boot "quiet".  By the time looking at a blank screen I wonder what's happening it's booted up.  Now Wondoze 7 on the same pc z z z z z z ....

Jerry

---

### Post by cariboo on 2011-07-10
I get a quick text message on shutdown on my Compaq Min i1100, so quick, I don't have time to read it, before plymouth starts up. On boot, the only text I see is the udev error

---

### Post by sgage on 2011-07-10
> **cariboo907 said:**
> Don't use the proprietary drivers. Plymouth works well on my nvidia system when using the nouveau driver, and the default Intel driver on my netbook. I plan on installing Lubuntu on an older HP laptop soon, so I'll see how the open source ATI/AMD drivers work.

The nouveau drivers have come a long way, but they're still not good enough, IMO. For a start, they cause the GPU to run significantly hotter than the nvidia drivers. There are also subtle rendering glitches. And the performance just isn't quite there for some apps, e.g., Stellarium.

Nouveau does, however, use a lot less RAM than nvidia. And you get a prettier boot process :KS

---

### Post by Xgen on 2011-07-10
I've always used the nvidia propriety drivers and always have graphical screens. With natty and burg installed, after choosing from the burg menu it remains on the menu for 5 seconds, switches to the ubuntu logo screen (nice graphics) for 3 seconds and then to a black screen with cursor for 2, then the desktop. Onieric does the same except for the udev text flashing momentarily and lightdm adding another 2 seconds. On shutdown though, sometimes it's graphical and others it's text.

---

### Post by rausuar on 2011-07-10
Well, i have a laptop with core i3 and intel HD graphics and still, the startup process shows TTY text, and dont mention the shutdown which is even uglier.  I understand the flixkering is a problem of the X, but I have seen, in some development discussions, that the TTY text in boot and shutdown can be, if not eliminated, hidden

---

### Post by Yes_It's_Me on 2011-07-11
Well there are a few issues with this. Xorg comes straight out of the 80's, where graphics on computer monitors was like black magic. Then we have the issue around graphics drivers (which is just insanely badly managed, by all parties). And then there are issues with compatibility and very buggy code.

---

### Post by VinDSL on 2011-07-11
Heh!  Boy, we're all over the place - every permutation possible...

I'm running Nouveau drivers / LightDM, and getting butt fugly text on startup, and a nice graphical shutdown.  LoL!

---

### Post by xebian on 2011-07-11
> **rausuar said:**
> Well, i have a laptop with core i3 and intel HD graphics and still, the startup process shows TTY text, and dont mention the shutdown which is even uglier.  I understand the flixkering is a problem of the X, but I have seen, in some development discussions, that the TTY text in boot and shutdown can be, if not eliminated, hidden

You should try suspend/hibernate instead.

Fast shutdown for me is just turn off main switch - no waiting. :)

---

### Post by johnnybelfast on 2011-07-11
Breezy Badger and Dapper Drake seemed to have a better looking start up... Now I'm getting a purple background with the Word Ubuntu in plain text. Why have we digressed so much since the days of Dapper?

---

### Post by akand074 on 2011-07-11
I have a nice boot/shut down most of the time with open-source ATI drivers. Usually as soon as I install the proprietary ones it gets bad. Startup is still graphical, no text, but it's like at a stupid resolution, blurry or hangs at a black screen until the boot finishes then shows the Ubuntu logo for a second before logging in. I get text during shutdown. Personally I prefer a full text boot (i.e login via text too then startx). But that's had problems in natty so I stopped using it for now.

---

### Post by psusi on 2011-07-11
They did this in Natty.  Grub now switches the monitor to its native resolution and plymouth takes over showing the splash screen until X comes up.

---

