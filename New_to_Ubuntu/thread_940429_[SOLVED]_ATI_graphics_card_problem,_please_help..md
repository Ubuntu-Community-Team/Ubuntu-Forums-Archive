---
title: "[SOLVED] ATI graphics card problem, please help."
date: 2008-10-07
forum: New to Ubuntu
---

### Post by xreaper on 2008-10-07
Hey guys.. just me here again. I have been at this problem for a little while now, searching up and down forums trying to find a solution. 

I am almost certain that it is a problem with my graphics card, (ati radeon x300) if that helps.

anyway, to the point:
&#65279;when I try to run any application that involves graphics, such as unreal tournament or regnum online, the window that I am trying to run gets this 'chopping' effect. this only happens when compiz is enabled. also, when I enable screensavers, after the screensaver comes up, when I move the mouse to try and get back to the desktop, the screensaver just plainly 'freezes'. I can still move the mouse, but cannot access anything and have to restart the x-server.

someone please help, I have tried looking at other peoples forums, and realising that this is a common problem, but using other peoples advice for other systems doesn't seem to help my situation.

any help will be much appreciated.

---

### Post by xreaper on 2008-10-07
Also, I am using the EnvyNG driver for my system. (ubuntu 8.04)

---

### Post by anewguy on 2008-10-07
First, I'd look at /var/log/Xorg.0.log.  If you search down through it you should be able to see if it is actually loading the driver correctly.

For choppy effects with compbiz on, I'd be suspicious of the power of your video card and the specs of your system.  Since I am not familiar with your video card, could you please post back the following:

[LIST]
[*]The specs for your computer - cpu, memory, etc.
[*]The specs for your video card.
[/LIST]

We can try to go from there.  If it were me, and I was trying to play any game beyond something simple like solitaire, etc., I would not have compiz enabled when I play it, especially if the game is graphics intensive.

Dave :)

---

### Post by xreaper on 2008-10-07
Hey, the specs are:
2.05ghz processor, 1gb ram, 128mb graphics card.What I've done now is uninstalled the envyNG driver and trying to see if everything that I use in my system will run correctly, so far, compiiz seems to be doing okay.

---

### Post by patrickballeux on 2008-10-07
This is a known problem that Compiz with opengl games are not a perfect match. 

There was a setting that you could put in your xorg.conf file so that playing your games fullscreen was working even with compiz on.
```

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
	Option "TexturedVideo" "on"
        Option "XaaNoOffscreenPixmaps"
        Option "UseFastTLS" "2"
        #Option "RenderAccel" "true"
	BusID       "PCI:1:5:0"
EndSection

```

I just don't remember which settings was enabling this but it is one them by setting them at on or off...

About your problem after screen saver where you can move your mouse but nothing really happen, I have this problem also.  In fact, if you use a 3d (opengl) screen saver, it seems that the prompt for your password is not shown.  But move your mouse in the middle of the screen, you should see the pointer change to a text pointer.  Simply enter your password blindly, press enter and you're back into your desktop.  

Me, I simply selected a non opengl screensaver to avoid this problem and compiz is off most of the time.  I simply enable it to show what it can do.

ATI card are not really good with Compiz compared to NVidia.  

I have a X1200 and have the exact same problems as you have.  

Good luck!

---

### Post by xreaper on 2008-10-07
ahh. Thanks for that last comment. Guess I'm going to have to do some upgrading to fix this issue then huh.

---

### Post by patrickballeux on 2008-10-07
If you can put a NVidia card, do it, you'll save hours of frustrations...

My laptop has an ATI x1200 and I can do with it, but I envy my desktop with the NVidia card where everything works so well.

But if I remember well, even in Windows, ATI card always had all kinds of problems...

There is somethings wrong about their graphic cards...

---

### Post by xreaper on 2008-10-07
lol, well they are reasonably cheap for size. I'll look into it. thanks for you advice.

---

