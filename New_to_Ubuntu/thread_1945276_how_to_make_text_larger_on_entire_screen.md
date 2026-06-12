---
title: "how to make text larger on entire screen?"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-22
Hi -

I'm not sure whether this is an ubuntu question or not, but it's a cinch that the support staff at the company who makes my monitor can't help with it.

I've got an LG E2290 monitor. In the display settings, the only resolution for 16:9 is the maximum 1920x1080. My old eyes just can't read the fine print when the display is set to this, but all the other options result in a distorted aspect ratio.

Is there any 3rd-party software that can give me a lower 16:9 resolution, or do I just need to sit closer to the screen?

Thanks.

---

### Post by PhantomTurtle on 2012-03-22
Look here for a guide on how to change font sizes: [http://www.installubuntulinux.com/2011/09/howto-change-system-font-sizes-in.html]("http://www.installubuntulinux.com/2011/09/howto-change-system-font-sizes-in.html"). You need the gnome tweak tool for it. (this is a tutorial for ubuntu 11.10 with gnome 3).

---

### Post by mzimmers on 2012-03-22
Thanks for that app...this is a very good start. I'd still like to reduce the screen resolution, so that various apps (like Chromium and Qt) would automatically have bigger fonts, too, but perhaps that's not feasible?

---

### Post by Megaptera on 2012-03-23
Hi,
Have you considered Vinux? It has some useful screen tools pre-configured.
Quote: "Vinux is a remastered version of the Ubuntu Linux Distribution optimised for visually impaired users. It provides a screen-reader, full-screen magnification and support for Braille displays out of the box! It can be run from a Live CD without making any changes to your hard drive. If you like it you can install it to a USB pendrive or to your hard drive either alongside Windows using the Virtual Version, or as a complete replacement for windows." [http://vinuxproject.org/](http://vinuxproject.org/)

Hope this is of interest?

---

### Post by mzimmers on 2012-03-23
Thanks for the suggestion, and I'll take a look at it. Really, though, I was hoping for a fix on a smaller scale (so to speak)...I just wanted a little less screen resolution. I find it more than a trifle annoying that LG only offers one resolution option with the correct aspect ratio. Ah well...

---

### Post by grahammechanical on 2012-03-23
I messed up some how and double posted. The second post is the best of the two. Sorry.

---

### Post by mzimmers on 2012-03-23
No video card; I'm using whatever is built into the ASRock Z68M-ITX/HT motherboard.

Will the universal access tool help with 3rd party applications too?

---

### Post by grahammechanical on 2012-03-23
Instead of thinking about changing the screen resolution try going to System Settings and using the Universal Access utility to change the text size.

Most applications have a zoom option under their View menu that will increase the text size.

Do you dual boot? Is the text size in the menu too small? I find it so. I have installed Grub Customizer.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

That will let you change the text size in the boot menu list to something  a lot larger. Like it is running the screen at a low resolution but not.

Otherwise go to System Settings-Displays Utility or if you are using a proprietary video driver installed through Additional Drivers, use the configuration utility that was installed with the driver.

I do think it best to resolve this without changing the screen resolution because the optimum setting is just that, the optimum.

Regards.

P.S. I have been experimenting. Universal access Changes the text size in the System Utilities. It may take a re-boot to find out if it does the same to the text in the top panel. You may be able to change the log in screen text size at the log in screen itself.

---

### Post by mzimmers on 2012-03-23
Good suggestions...thanks. I will definitely look into the grub customizer. Whoever chose the font size for that must have eyes like an eagle.

EDIT:

I tried the instructions for using USC: added the source, but USC still can't find grub-customizer. I notice the link is over a year old; has it become unavailable?

EDIT again: I downloaded Synaptic, and installed it that way. MUCH better. Odd that USC couldn't find it, though.

Thanks for the help.

---

