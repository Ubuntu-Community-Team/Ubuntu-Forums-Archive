---
title: "On Karmic Now But With A Few Hiccups"
date: 2009-11-03
forum: Philippine Team
---

### Post by randytan on 2009-11-03
Hi All!

I successfully updated my office unit to Karmic but am experiencing a few hiccups.

My weather and temperature icon near the clock has vanished even if I checked it in the preferences. Actually, this was also observed when I re-installed Jaunty before this upgrade.

The status icons in some displays of Pidgin are missing. This is when you right click on the icon and try to change your status from there. It usually displays the icon (whether available, busy, away, etc.) but now, it doesn't.

Same is noticed when you click on your log in name at the rightmost top part of your screen, the icons cannot be seen.

As before, my unit's built-in camera still does not work but it's not really a biggie for me though it would be nice if we could get it working.

Now, I'm working from the restart after the upgrade so I'm not sure if all of this will be resolved, but in the even that they are not resolved, can anyone help me out?

So far though, things are running great.

Hope to hear from y'all on this soon.

:)

---

### Post by aljoriz on 2009-11-03
Using Karmic 64bit here.  

May bug talaga ang 64bit 9.10 it would say that ECC modole of the system was not loaded and the system is unstable.  

I have informed the developers via approot, turns out that this is a HIGH instance bug.

******
As for your camer try the following
( I assume that you use your camera for skype)

If you are running 32bit
Go to terminal
$ sudo gedit /usr/local/bin/skype

then copy paste the following
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

press the save icon, close the gedit window and go back to the original terminal where u did gedit

write
$ sudo chmod a+x /usr/local/bin/skype 

I hope this helped

---

### Post by wersdaluv on 2009-11-03
Did you already set your location on the clock applet? You need to do that for the applet to know what location's weather to report.

Pidgin's right click menu and a lot of other things lost their icons. That's the new default setting for this version of GNOME. To change that, go to the "Appearance" dialog, on the "Interface" tab, check "Show icons on menus."

What's your webcam? What's the output of lsusb?

---

### Post by randytan on 2009-11-04
Hi All!

@wersdaluv, you hit the nail on the head with your post. Now I once again have the icons and the weather report. I find it strange as I though I had set the location before :oops:

As for Isusb, how do I find that out? I want to try this out first before I go with what aljoriz suggested. The camera is a built in unit on my company issued notebook, an Acer TravelMate 3270.

Thanks again! :D

---

### Post by wersdaluv on 2009-11-04
> **randytan said:**
> Hi All!

@wersdaluv, you hit the nail on the head with your post. Now I once again have the icons and the weather report. I find it strange as I though I had set the location before :oops:

As for Isusb, how do I find that out? I want to try this out first before I go with what aljoriz suggested. The camera is a built in unit on my company issued notebook, an Acer TravelMate 3270.

Thanks again! :D
Just run **lsusb** on the terminal then post the output here :)

---

### Post by pinoyskull on 2009-11-04
Karmic Koala runs fine on a Dell D520, niiiiiiice!

---

### Post by Ravskie on 2009-11-04
> **pinoyskull said:**
> Karmic Koala runs fine on a Dell D520, niiiiiiice!

i seconded sir pati sa Dell Desktop it is cool !

---

### Post by badrra on 2009-11-04
Nasubukan ko na Koala Xubuntu and surprisingly 2x faster than Jaunty on the same machine. It is as fast as Puppy linux actually so I will stick to it for now. 

So far I am not seeing any issues with it. Tried Compiz but I'd rather have ther egular one kasi medyo mabagal sya sa system ko. 

OPERA rocks and I definitely switched to it and finally gave up on Firefox. 

Tried Opera 10.10 as well. No difference i performance. I will check the server capability of Opera 10.10 later. 

Overall i am impressed.

---

### Post by pinoyskull on 2009-11-04
Empathy doesn't have OTR support, back to Pidgin :D

---

### Post by randytan on 2009-11-05
> **wersdaluv said:**
> Just run **lsusb** on the terminal then post the output here :)

Thanks wersdaluv ;)

This is what I got:

[INDENT]Bus 001 Device 102: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/INDENT]

---

### Post by randytan on 2009-11-05
By the way, the included Firefox version now works WAY better than the one in Jaunty. :KS

My current complaint about Karmic is that it takes forever to start up! :mad:

In fairness to the Koala though, it works a whole lot faster than the previous versions and has a lot of enhancements. ;)

---

### Post by pinoyskull on 2009-11-05
> **randytan said:**
> By the way, the included Firefox version now works WAY better than the one in Jaunty. :KS

My current complaint about Karmic is that it takes forever to start up! :mad:

In fairness to the Koala though, it works a whole lot faster than the previous versions and has a lot of enhancements. ;)
that's odd, mine loads fast

---

### Post by jsgotangco on 2009-11-05
Yeah my old laptop is actually fast.

---

### Post by randytan on 2009-11-07
Speed wise after start up, I can't complain. It is really fast.

It's the speed at start up after I hit the on button is what is slow until after you input the password. Then it's wait a while longer, then I'm in.

Like I mentioned above, after all this drama, works fast again. ](*,)

---

### Post by perbiu on 2009-11-07
Currently the best release ever, it also fixes my laptop issues, but my Smartbro ZTE mf622 plug it no longer works. So i switched back.

---

### Post by wersdaluv on 2009-11-07
> **randytan said:**
> Thanks wersdaluv ;)

This is what I got:

[INDENT]Bus 001 Device 102: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/INDENT]
Sorry ngayon lang. 

Sabi dito [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271258](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271258) 046d:0896 Logitech, Inc. OrbiCam (sa post #40), ok na raw sa skype.

---

### Post by badrra on 2009-11-08
Tweaked compiz a little bit, worked a little faster. I actually played around with the refresh rate. certainly works faster now. 

I still have one problem. I still can't install the linux version of Heroes of Newerth. Its giving me all sorts of errors especially the script. I guess I'm giving up on it for now. I can still run the regular DOTA anyway.

Tried Opera 10.10 server capability. Makes it a lot easier to set up a web server by merely subscribing to Opera Unite. Also I can make a steaming server out of that. And also pictures btw. But its really no big deal.

---

### Post by randytan on 2009-11-09
> **wersdaluv said:**
> Sorry ngayon lang. 

Sabi dito [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271258](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271258) 046d:0896 Logitech, Inc. OrbiCam (sa post #40), ok na raw sa skype.

That's weird, when I check with Skype, it says no devices found. :-k

---

### Post by Script Warlock on 2009-11-09
sa network manager ng 9.04 yun ang hiccups ko na di ako pinatulog eto kaya 9.10 wala na problema sa ics?. gusto kong subokan pero may bugs daw sa ipmasq so cguro hintay na lang muna ako next release nila.. so far sa laptop at workstation ko ok pa naman after the clean install wala pa namang problema na-encounter sa slowdown at bugs.. bilis ng boot at shutdown..

---

### Post by specialcowboy on 2010-01-20
> **aljoriz said:**
> Using Karmic 64bit here.  

May bug talaga ang 64bit 9.10 it would say that ECC modole of the system was not loaded and the system is unstable.  

I have informed the developers via approot, turns out that this is a HIGH instance bug.

******
As for your camer try the following
( I assume that you use your camera for skype)

If you are running 32bit
Go to terminal
$ sudo gedit /usr/local/bin/skype

then copy paste the following
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

press the save icon, close the gedit window and go back to the original terminal where u did gedit

write
$ sudo chmod a+x /usr/local/bin/skype 

I hope this helped

I was having problems with my webcam as well.
Your fix for the Acer Orbicam 046d:0896 worked like a charm! My webcam worked with Cheese but not with Skype. I was getting strange green lines and image ghosting.  Tried your fix and now my webcam works great with Skype. Thanks! :D

---

### Post by aljoriz on 2010-01-21
^ Glad to be of help.  I learned that trick from a site also.  I'm just giving back what was given to me.

---

