---
title: "[SOLVED] Compizconfig setting mystery! [Noob XING]"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by TheeMaverick on 2008-08-30
Decided I was tired of Windows! Two days ago I setup Ubuntu and struck the coup de grace to XP. I consider myself fairly PC savvy, but I never got into Linux. This command line (terminal) circus, mixed with my fuzzy understanding of how an OS works, makes for hours of forum browsing for me! Finally gave up with this one... 

Installed Compizconfig through apt-get command. 

Seemed to go smoothly, I can open the program through system -> preferences etc.
I try to mess with opacity settings, nothing happens. I slide that bar up and down. -No change. 
Hit the (NEW) button
I type into Opacity Windows: type=dropdownmenu, or dropdownmenu. -nothing
I tried this...

(name=Vista) | (name=gimmie_applet) | (name=gnome-panel) | (type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog) -18621

Unsure of exactly of what the name= is for but nothing happened. Just copy and paste because the theme instructions told me to.

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)
This helped me a little bit, but I might as well be reading Chinese. 

Sliding bars up and down, closing program, restarting, all that jazz. No change. 

Any help or guidance would be appreciated.

---

### Post by Eredeath on 2008-08-30
this might seem silly... but did you enable it by using the assigned key-strokes? usualy super+ something

---

### Post by nicedude on 2008-08-30
do you have your desktop effects set to extra which is required to get any compiz 3d type effects to work. If not try right clicking on your desktop and selecting "change desktop background" and then select "visual effects tab" and then hit "extra" if it wont work then you either have a graphics card that is not compatible or a graphics card driver that is incompatible.

If you have Nvidia or ATI graphics in general then you just need a better driver to make "extra" work. Try envyng-gtk in the repositories.


Hope this helps you figure it out

---

### Post by TheeMaverick on 2008-08-31
The "extra" setting is not on, which would probably explain why the 3d effects are not working. I did download EnvyNG, but it couldn't detect the correct drivers. My card is an ATI® Radeon™ IGP 345M. I did a brief search, and supposedly it is difficult to get the 3d acceleration working on Linux. 

This poor laptop probably couldn't handle it much anyways. I'm satisfied in finding the root of the problem. Thanks for your help! My emergence into the Linux community has been amiable. Think I just might stick around!

---

