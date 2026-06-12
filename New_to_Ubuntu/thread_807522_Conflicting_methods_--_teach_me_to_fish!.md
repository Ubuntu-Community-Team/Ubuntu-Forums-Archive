---
title: "Conflicting methods -- teach me to fish!"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-05-25
Teach someone how to fish, help them feed themselves for the rest of their lives!

So could someone please explain how each of these several methods for changing and setting screen resolutions work?

Problem: Setting screen resolution for one / several monitors.

1. Modifying xorg.conf directly (Device, Monitor, Screen sections)

2. gnome-display-properties

3. 910resolution

4. Running Applications -> Other -> Screen and Graphics utility.


Please help! I've spent two weeks searching through the forums and trying all the above methods with partial success. If I can know which of these are the same / conflict, it'd be of great help!! I've only found "To Do" list of steps to follow -- that is like charity while answering this would teach me to fish for myself!

---

### Post by ardvark71 on 2008-05-25
Hi...

I'm going to make a somewhat educated guess here as to a general difference between them....

the xorg.conf file is the base foundation of your graphics driver and settings while the other programs are GUI frontends (with the exception of 910resolution, I've not dealt with that one, so no idea) to more easily and quickly make many of the same changes you would through xorg.conf. 

An exception would be that driver changes are done through xorg.conf. I've had to change Nvidia drivers this way.

Best Regards...

---

### Post by ingrid_ozikem on 2008-05-26
Thanks for that reply! You seem to be right about

1.Applications -> Other -> Screen and Graphics utility  ---- just a GUI for changing xorg.conf. Must restart X for changes.

But these do NOT seem to change xorg.conf at all,

2. 915resolution -- recommended in many many threads for Intel video cards (common in laptops). Man page says 
"915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets."

3. gnome-display-properties (found in Sys. -> Pref. -> Screen Resolution)

Understanding the last two would be very useful to those of us looking to configure more complicated setups with multiple monitors etc. Thanks!!

---

### Post by |Eric| on 2008-05-26
actualy most of these Change the xorg.conf witch is part of the X server (its basicaly the config file for it) 

Keep in mind that when the Windowmanager is loaded it can make request to change the video parameters to the X server so those utilities can change that too.

but usualy most utilities change the Xorg.conf (the one that the Xserver is currently using )

xorg.conf is not part of the video driver as the videodriver is part of the kernel (linux itself) or added to it 


i usualy go mod the xorg.conf directly as its pretty strait foward for most of the cases

---

### Post by ingrid_ozikem on 2008-05-26
Thanks. I'll buy your answer of Windowmanager requesting changes the video parameters to the X server for gnome-display-properties. It certainly does NOT change xorg.conf but perhaps does what you say.

But I really seem to need 915resolution -- changing xorg.conf seems to work for NVidia and ATI cards but I have an Intel chipset video card (many laptops do).

What does it mean for the man page to say "*_915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets._*"

Is that different in nature from changing xorg.conf and sourcing it?

---

### Post by ardvark71 on 2008-05-26
> **ingrid_ozikem said:**
> Thanks. I'll buy your answer of Windowmanager requesting changes the video parameters to the X server for gnome-display-properties. It certainly does NOT change xorg.conf but perhaps does what you say.

But I really seem to need 915resolution -- changing xorg.conf seems to work for NVidia and ATI cards but I have an Intel chipset video card (many laptops do).

What does it mean for the man page to say "*_915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets._*"

Is that different in nature from changing xorg.conf and sourcing it?

Hi...

Honestly, I am learning this right along with you. :)

Here is a aite that goes more in detail concerning this program...

[http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/](http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/)

I'm guessing you're having problems with your resolution, size, 3D rendering, etc., because your system is using Intel graphics with Ubuntu "straight out of the box."

Your version already may have 915 already installed but in case not, you can use Synaptic to download the program from the repositories, according to the information from the above link.

Hope this helps.:)

Best Regards...

---

### Post by jw5801 on 2008-05-26
> **ingrid_ozikem said:**
> Thanks. I'll buy your answer of Windowmanager requesting changes the video parameters to the X server for gnome-display-properties. It certainly does NOT change xorg.conf but perhaps does what you say.

But I really seem to need 915resolution -- changing xorg.conf seems to work for NVidia and ATI cards but I have an Intel chipset video card (many laptops do).

What does it mean for the man page to say "*_915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets._*"

Is that different in nature from changing xorg.conf and sourcing it?

It's entirely possible that 915resolution is a tool for changing bios (firmware) level options for your video card.

So a summary would be:
**gnome-display-properties:** Desktop Environment level settings (Gnome requesting that the X server change something)
**Xorg.conf (& Screen+Graphics Utility):** X server level settings (settings that appear as soon as the X server is started, ie your login screen)
**915resolution:** hardware/firmware level options and settings for intel video cards (OS independent)

So gnome-display-properties could be useful for a multi-user setup, otherwise Xorg.conf is probably the best, or most hardware independent, way to go. 915resolution is for changing bios level options specifically for your video card.

---

### Post by ingrid_ozikem on 2008-05-26
Thanks for those replies!  What you guys say about 915resolution does seem right. But while poking around, I found one important LIMITATION of xorg.conf when it comes to Widescreens and Intel cards. You need 915resolution in this case.

Usually, the resolution modes you create in xorg.conf through ModeLines are read by the driver and understood. But apparently the i810 driver IGNORES these modes. If you try to set a mode you define in xorg.conf, i810 will simply ignore it and use a pre-defined mode. (This happens for Widescreen modes.)

The only way for i810 to learn about a new mode is for that mode to be set in the BIOS. That's where 915resolution comes in. Use it to create a new mode in the BIOS and then load it with xorg.conf.

i810 is a commonly used driver for Intel graphics cards (common on laptops). The driver 'intel' is apparently better, newer and doesn't have the above problem but I find it hard to get a dual monitor set up with 'intel'. 


Bottom line: if you want to use i810, you might be forced to use 915resolution since modes cannot be created using xorg.conf.

---

### Post by ardvark71 on 2008-05-26
> **ingrid_ozikem said:**
> Thanks for those replies!  What you guys say about 915resolution does seem right. But while poking around, I found one important LIMITATION of xorg.conf when it comes to Widescreens and Intel cards. You need 915resolution in this case.


Right.:)

I do wish, however, that hardware manufacturers would write their drivers for ALL operating systems and/or at the same quality level rather than force Linux developers and programmers to reverse engineer a lot of it. :(

Best Regards...

---

