---
title: "Boot @ 60hz without xrandr -r 60?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by lemmiwinks2 on 2014-06-06
Can anyone tell me how to always boot at 60hz without having to type 'xrandr -r 60' in the console after every boot?  Why isn't this an option??

Secondly, why isn't there a clear, concise, easy method to install a video card driver?  I've tried two different guides and they both blew up my installs (Ubuntu once, and Mint once).  I have an ATI Radeon HD 5700 Series card.


Rant:  

This single issue should be what the Linux community should focus on until fixed.  

NOTHING IS MORE AGGRAVATING THAN VIDEO ISSUES AT INSTALL.  NOTHING.

Nothing will chase away new users faster than being unable to read the damn screen.

I'm close to giving up and buying a Mac.  I am literally blown away that video cards are still such an issue with Linux.  Shaaaame on, well, someone out there.  :?

---

### Post by Luke M on 2014-06-06
I'm curious, 60Hz as opposed to what? Usually people have the problem of getting 60Hz when they want something else.

Rant reply:
Video cards are very complex. AMD and Nvidia have huge teams of engineers developing Windows drivers. The resources that can be put into linux, with its 1% market share, is naturally less. Plus whatever volunteers are able to contribute.

 Also, the linux guys don't care about closed source drivers. They don't intentionally block their use, but neither do they try to make it painless. This is rather stubborn of them, but it does pay long run dividends since it encourages hardware manufacturers to contribute to linux.

---

### Post by deadflowr on 2014-06-06
Which driver did you finally install?
Do you have catalyst installed?
Open it and set the display there.

Is your monitor supported?
(I mean can the system properly read the monitor's edid, look in /var/log/Xorg.0.log, usually when the system can't read the edid, it's noticeable in the log file)

---

### Post by grahammechanical on 2014-06-06
There is an easy method of installing video drivers - use the Additional Drivers utility.

The problems are caused by the proprietary nature of the drivers which prevents Ubuntu developers from accessing and modifying the driver code. FOSS developers work hard developing open source drivers - Nouveau for Nvidia cards and Radeon for AMD/ATI cards. The issue these developers face is the proprietary nature of the hardware.

From time to time I test ISO images and I will not risk a broken install by ticking the "install third party software" box. Doing that will bring in a proprietary video driver. I recommend not ticking that box and after the installation has finished and resulted in a re-boot to a desktop, then to install Ubuntu Restricted Extras and using Additional Drivers to experiment with proprietary video drivers. And I do mean experiment. This is how I see the situation. But I do not blame free and open source developers.

---

