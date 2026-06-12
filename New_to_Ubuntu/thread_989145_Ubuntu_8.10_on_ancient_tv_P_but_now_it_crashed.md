---
title: "Ubuntu 8.10 on ancient tv :P but now it crashed"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Spanklord on 2008-11-21
k so i actually have to questions. 
i just installed ubuntu 8.10 on a crappy pc i had lying around( 1.6 ghz and 512 ram with some ati card) and i only have a very old sony tv screen at my disposal so i linked it up with the yellow cable thingy :P 

Problem 1. 
i tried changing the resolution then my screen got totaly distorted and it didnt switch back to normal after 20 sec or something ( dont think i pressed anything but i might have had )
ps. the boot screen still looks fine so basicly . how do i reset to the default resolution / refresh hrate etc.

Problem 2. 
well the reason i was trying to change the resolution in the first place was that it looks epicly crap. the cable that i also have connected to my tv has a way better resolution so its not the incapability of my tv. but is there any software so i can try testing other resolutions or that will get it to look just a bit nicer. 


tnx in advance

---

### Post by markjensen on 2008-11-21
Ahhh.  "epic": the noun, adjective and adverb of choice of my kids, too.

Is the "yellow cable thingy" an 'RCA' style video cable or an S-video cable?  And connected to a real TV?   Or is this just an old monitor with a VGA cable that happens to be colored yellow?

A TV will only allow a specific resolution.  You cannot just bump it up or down and expect things to work.   Did it ever work at any setting?  And what did you set it to when it unworkable?

As for testing other resolutions, once again, you are going to be pretty much stuck matching an NTSC TV signal.   Sorry, but it will be very low resolution.

---

### Post by Jive Turkey on 2008-11-21
When you are looking at the garbled screen wondering how to get your old resolution back press ctrl+alt+F2  (any "F" key will work except F7 I believe which actually corresponds to your active running garbled console).

That should drop you to a text login prompt. If not try a different F-key. Enter your username and password.  Then at the prompt:

```
sudo nano /etc/X11/xorg.conf
```

This will open a primitive text editor to modifiy the file that may have your resolution settings in it.

There are many threads here with examples of the syntax and layout of the xorg.conf file.  Figure out what the NTSC defaults are and set it to those.  Once you are done, press ctrl+x type y to save and hit enter.

then back at the prompt, type :
```
sudo /ect/init.d/gdm restart
```
and then
```
startx
```
Which should restart your window manager and bring you to your desktop.

Good luck, it to me a week to learn how to do that crap when I needed to.

---

### Post by Spanklord on 2008-11-21
markjensen 

yes indeed an RCA cable. and well when you asked if it worked on any setting. it did work on my windows but still very vague. 


i just started reinstalling caus. well . i already lost like 1 hour just trying to figure this out but im fairly positive im gone run into the same problem in 20 min :P. 2 new questions

1. Why is my resolution so limited when im sure the normal tv signal is a decent resolution. 

2. So is there any way that ubuntu goes back to its uterly default configuration. i tried all the xorg.conf editing and dpgh-reconfigureing i found with google but none put it back in its orriginal way 


ps other intersting information. i hooked up a normal pc monitor and it gave the same distortion 

epic

---

### Post by markjensen on 2008-11-21
I have not played with hooking a computer up to a TV since my Atari 800XL days.

And NTSC isn't all that "decent" by todays computing standard. [648x486](http://www.strata.com/support/3dmanual/ch13/ch13_7.html) seems to be what is commonly accepted as NTSC TV.

And, yes, you can step through the listed resolutions, using CTRL+ALT+[num pad plus] or CTRL+ALT+[num pad minus].  But if your xorg.conf file lists a lot of resolutions not supported by your card and TV, then you will have a lot of stepping to do.

---

