---
title: "How do I change screen size"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by schmitta on 2014-07-17
I got a notice from ubuntu that 12.04 was no longer supported and that I needed to upgrade which it supplied a link to do. I upgraded and restarted my system. Now the screen size is 1920X1280 and I am old and can't read the screen. I tried to use SYSTEM>APPEARANCE but it does not allow me to change the screen size to a lower value. How do I lower the screen size? Thank you.

---

### Post by AnotherKevin on 2014-07-17
These settings should be found under display/monitor.  It will be a hardware adjustment, not appearance.  Hope this is a help...

Kevin

---

### Post by TheFu on 2014-07-17
On any Linux system running X/Windows, the X/Windows screen size can be controlled through the **xrandr** tool.  Often, different GUIs will have a slightly different GUI front-end and allow saving the setting - LXDE uses **lxrandr**, others use **arandr**, and so on.  The manpage for xrandr is fairly clear, so if anything non-trivial is desired, it explains.

Of course, Unity has a way to control this too ... er ... somehow. Knowing the standard method will help people who prefer to know 1 way to control it, regardless of GUI installed.

---

### Post by schmitta on 2014-07-17
Thanks to all -- You help a very young old man!

---

### Post by at_first_light on 2014-07-18
It appears your problem is solved. To summarize (with additional details) what has already been said there are a couple ways to do it.

**_Option #1:_**

In the terminal you can use randr to set the screen resolution.

```

xrandr --size 1024x768

```

The above code will change the screen resolution to a width of 1024 pixels, and a height of 768 pixels.

_**Option #2:**_

[ATTACH=CONFIG]254808[/ATTACH]

There is an option for changing display resolution in system settings. Go to the cog in the top right of the desktop screen, from the menu choose "system settings", and click on "Screen Display". You can then change your screen resolution, and apply it.

---

