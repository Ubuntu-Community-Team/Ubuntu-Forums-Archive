---
title: "Widescreen monitor - no proper resolution?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by siriusbg on 2012-01-03
Hi. I bought myself a 23 inch Dell monitor, but from the options available at the Nvidia X Server settings, there is no resolution that suits me. I have a Windows installed, where I chose the 1280x720 resolution. 
I tried creating it with xrandr, following the guidelines at help.ubuntu.com, but I didn't succeed. Also, editing the monitors.xml file had no effect and the resolution is the same after I rebooted. 
Could anyone give me a hint?

---

### Post by xtjacob on 2012-01-03
You could try running ```
sudo nvidia-xconfig
``` to regenerate a new x config file, that might fix it.

---

### Post by mcduck on 2012-01-03
What is the actual (native) resolution of the display? It's most likely more than 1280x720 which sounds rather low for a 23" monitor...

I would really suggesting using the native resolution, and if you find it too high for you then increase the font size (or DPI/font scaling) instead of reducing the resolution (As LCD displays can only show the one and single resolution they were built for, everything else is simply scaled into that resolution and the result is usually pretty bad quality...)

---

### Post by siriusbg on 2012-01-04
Well, the actual resolution is 1920x1080, but it is really too much for me and the refresh rate is only 60Hz. Btw, it's a LED monitor, in case this helps.
 I really can't figure out why the xrandr command doesn't work. Also, the xorg.conf file seems to be empty when trying to open it. 
I'm getting really disappointed with Ubuntu - nothing seems to be working unless you configure it on your own. I can't even create desktop shortcuts without some tweaking, all the torrent clients are giving me errors, I can't even open a text file in my native language due to encoding problems...

---

### Post by bluexrider on 2012-01-04
> **siriusbg said:**
> Well, the actual resolution is 1920x1080, but it is really too much for me and the refresh rate is only 60Hz. I really can't figure out why the xrandr command doesn't work. Also, the xorg.conf file seems to be empty when trying to open it. 
I'm getting really disappointed with Ubuntu - nothing seems to be working unless you configure it on your own. I can't even create desktop shortcuts without some tweaking, all the torrent clients are giving me errors, I can't even open a text file in my native language due to encoding problems...
Try a different distro, perhaps Linuxmint or Pinguy

---

### Post by siriusbg on 2012-01-04
But I'd really WANT to stay with Ubuntu - I like the looks of it, the idea and this community that convinced me to install Ubuntu. That's why I want to deal with these problems and enjoy my work under this Linux distribution. So that is why I bother you with asking these questions - they may seem easy or stupid for you, but I've got Ubuntu since 8.December 2011..

---

### Post by Johnny3 on 2012-01-04
What don't you like about 1920x1080? 60Hz is good.I run my like that and use Advance Settings to make my fonts bigger.
Good Luck and God Bless Johnny3 65+++

---

### Post by mcduck on 2012-01-04
> **siriusbg said:**
> Well, the actual resolution is 1920x1080, but it is really too much for me and the refresh rate is only 60Hz. Btw, it's a LED monitor, in case this helps.
 I really can't figure out why the xrandr command doesn't work. Also, the xorg.conf file seems to be empty when trying to open it. 
I'm getting really disappointed with Ubuntu - nothing seems to be working unless you configure it on your own. I can't even create desktop shortcuts without some tweaking, all the torrent clients are giving me errors, I can't even open a text file in my native language due to encoding problems...

Then why not just set a larger font size to make the user interface more suitable for your taste, without sacrificing the image quality like using a wrong resolution on a LCD screen does?

(It makes no difference if it's a LED monitor or not. The picture still comes from LCD screen, the LEDs are just used for the backlight. Besides, if the image was actually made using the LEDs it would have a native resolution exactly for the same reasons LCD screens have one, there is a certain amount of pixels physically built into the panel. And only having a 60Hz refresh rate is normal as well, you'll rearely see anything higher than that on a LCD screen, and having a higher refresh rate wouldn't even make any visible difference as the LCD screen isn't completely redrawn each frame like old CRT displays work. You'll usually only see higher refresh rates on active 3D displays...)

Anyway, there is no xorg.conf by default, the file isn't needed as all configurations are detected automatically instead. You can still create the file and add settings there if you want to. It's pretty hard to say anything about why your xrandr command didn't work without seeing the actual command you used, so you might want to post it here if you want people to help with that... :)

---

### Post by siriusbg on 2012-01-04
Ok, guys, I gave it a try and to be honest - it really isn't that bad. It's just... different. 1 week ago I had a 14'' CRT monitor, running on 800x600 and I had it for about 15 years. That's why such a resolution is a bit .. new and strange for me. I'll mark the thread as solved - thank you **mcduck** for providing that useful info :)

---

### Post by mcduck on 2012-01-04
> **siriusbg said:**
> Ok, guys, I gave it a try and to be honest - it really isn't that bad. It's just... different. 1 week ago I had a 14'' CRT monitor, running on 800x600 and I had it for about 15 years. That's why such a resolution is a bit .. new and strange for me. I'll mark the thread as solved - thank you **mcduck** for providing that useful info :)

No problem. And I'm sure you'll get used to the new display eventually. :)

...Also if you have any problems with the high resolution with things like web pages, you can set larger font sizes (or enable text scaling or text+images scaling) in the web browser. Or do what I do and use the [NoSquint]("https://addons.mozilla.org/en-US/firefox/addon/nosquint/") extension in Firefox, which allows you to configure the scaling options a bit better and also separately for each web site if you need to. That's what I'm using on my laptop as the 1920x1080 resolution on a 15" screen can sometimes make web pages a bit small...

(the only problem I'm having with the high resolution on a small screen is that I do sometimes need to use Windows, and it seems to really lack any proper ways to manage high DPI displays. Perhaps they'll some day copy that feature from Linux as well instead of their current claim that "scaling user interface is impossible". :D)

---

