---
title: "Xubuntu 14.04:  Display goes beyond edges of flatscreen tv when using output HDMI"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by queazy03 on 2014-04-28
Hi,

[http://imgur.com/ueNZ2BD](http://imgur.com/ueNZ2BD)
What can I do to make the displayed area NOT go beyond he edges of my flatscreen TV when I use the HDMI output?  
Is there a command in Xrandr that can fix this?  The Xrandr command "--scale XxY" did not work.

I have just build a new PC with Xunbuntu 14.04 as its only OS, but apparently my old pc monitor is broken so I am resorting to use my Flatscreen TV (Samsung LED Series 6000) as my screen.  The thing is when I attach the PC to the TV using the HDMI cable, the displayed area goes beyond the edges of the tv screen out of what I can see (please take a look at "[http://imgur.com/ueNZ2BD](http://imgur.com/ueNZ2BD)").  My TV is connected to my PC by using a HDMI cable that is plugged into my graphics card.

I thought if I used the Xrandr (manual at "[www.x.org/archive/X11R7.5/doc/man/man1/xrandr.1.html]("http://www.x.org/archive/X11R7.5/doc/man/man1/xrandr.1.html")") with its command "--scale XxY" I would be able to squish the screen so that it would fit inside the flatscreen's display area, but that didn't work.  All it really did was increase / decrease the resolution, but it still ALWAYS went beyond the edges of what you can see on the flatscreen tv.  Please see "[http://imgur.com/bGwVkTY](http://imgur.com/bGwVkTY)".  

"[http://pcpartpicker.com/p/3weiH](http://pcpartpicker.com/p/3weiH)" is a list of all my parts.  
"[www.samsung.com/us/video/tvs/UN40D6000SFXZA-specs]("http://www.samsung.com/us/video/tvs/UN40D6000SFXZA-specs")" is the Samsung webpage of my tv.
"[www.lg.com/ca_en/monitors/lg-W1934S-SN-lcd-monitor]("http://www.lg.com/ca_en/monitors/lg-W1934S-SN-lcd-monitor")" is the webpage about my old broken monitor (if anybody wants to take a chance at helping me try to fix that, see "[http://youtu.be/WjHldzY4cps](http://youtu.be/WjHldzY4cps)").

What can I do to shrink the display area of what should go on my screen, so that it can fit within the visible area of my flatscreen tv when I use it with my HDMI cable?  Thank you.

---

### Post by zemega on 2014-04-29
That is not Xubuntu fault. That's your TV fault. When using HDMI, some TV decide to enlarge the output a bit, so some of the screen edge are invisible. The same thing happens with Windows 7 as well. An alternative you can try in the mean time is, play around all the option on the TV and it will resize the edge properly. I think we have the same TV, not sure of the exact model, but after playing around the options in the TV setting, I manage to 'fix' the trimming situation.

P.S. : Its a Samsung TV as well.

---

### Post by papibe on 2014-04-29
> **zemega said:**
> That is not Xubuntu fault. That's your TV fault.
+1

It is called [overscan]("http://en.wikipedia.org/wiki/Overscan"). For most TVs you can correct it using your remote.

For example, in the case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Hope it helps.
Regards.

---

