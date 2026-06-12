---
title: "Ubuntu mini.iso won't boot in VirtualBox!"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by babydanks on 2011-10-22
So I have now tried to install the mini.iso for 11.04 and 11.10 with no luck in VirtualBox. When I boot for the first time, I either get a blank screen, or a white blinking cursor. 

On occasion, if I spam the keyboard I can get grub to load. From here I was able to get Ubuntu to boot successfully only twice by entering safe mode and then booting normally. 

Has anyone gotten this to work? Frustrating!

---

### Post by wolfen69 on 2011-10-22
Works for me. Are you sure you are booting to the mini.iso in the settings?

---

### Post by babydanks on 2011-10-22
UPDATE: So I did manage to get it to work with mini.iso Ubuntu 10.04. Why won't it work with the new versions of ubuntu minimal?

---

### Post by blazk on 2011-11-05
Same here :( Just tried to install 11.10 mini.iso. First 'basic ubuntu server' and later 'minimal Lubuntu installation' - none will boot after installation - I just see black screen!

---

### Post by gmargo on 2011-11-05
> **blazk said:**
> Same here :( Just tried to install 11.10 mini.iso. First 'basic ubuntu server' and later 'minimal Lubuntu installation' - none will boot after installation - I just see black screen!

Probably the black screen is there because Ubuntu helpfully switched you to virtual console #7, all ready for a graphical display manager.  Since you installed a server setup, this is less than useful.

To switch to console #1 within the virtualbox instance, use "Control-F1".

[http://wiki.debian.org/VirtualBox#Switching_consoles](http://wiki.debian.org/VirtualBox#Switching_consoles)

---

### Post by wolfen69 on 2011-11-05
> **gmargo said:**
> Since you installed a server setup, this is less than useful.

The mini iso is not a server setup unless you specifically added server components after install.

In a previous post in this thread, I mentioned that it worked for me. I meant that it booted up and installed, but after that,  I can not get to a command line to begin installing X, desktop environment, etc. 

But after some research, I hear that vbox is having some serious issues lately, and this may be one of the problems they are having. I've never had a problem before using the mini iso in vbox until now.

---

### Post by blazk on 2011-11-05
> **gmargo said:**
> Probably the black screen is there because Ubuntu helpfully switched you to virtual console #7, all ready for a graphical display manager.  Since you installed a server setup, this is less than useful.

To switch to console #1 within the virtualbox instance, use "Control-F1".

[http://wiki.debian.org/VirtualBox#Switching_consoles](http://wiki.debian.org/VirtualBox#Switching_consoles)

Brilliant! it switched me to the text login screen - thanks :)

---

### Post by JustinForce on 2012-04-09
> **gmargo said:**
> Probably the black screen is there because Ubuntu helpfully switched you to virtual console #7, all ready for a graphical display manager.  Since you installed a server setup, this is less than useful.

To switch to console #1 within the virtualbox instance, use "Control-F1".

[http://wiki.debian.org/VirtualBox#Switching_consoles](http://wiki.debian.org/VirtualBox#Switching_consoles)

This absolutely helped me, except it's Alt-F1, not Ctrl-F1. 

Thanks!

---

