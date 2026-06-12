---
title: "HOW TO: Create a Stargate on your desktop"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Warbo on 2006-08-29
I was testing some screen capture software, and thought I may as well do something cool with it, so here it is: [http://video.google.co.uk/videoplay?docid=-5285169537303773716&hl=en-GB](http://video.google.co.uk/videoplay?docid=-5285169537303773716&hl=en-GB)

You can also find this on [http://www.ubuntuvideo.com](http://www.ubuntuvideo.com) now as well.

The basic idea is:
a) Get an image of the Stargate from the TV series of the same name
b) Cut the centre of it out, then save it in a format like PNG which keeps the transparency
c) Use XTeddy to display the image without a window border and using XShape to cut the transparent section out of the window
d) Run XDesktopWaves to provide a wormhole-like effect inside the gate

The video tutorial walks you through this, but the screen capture tool (PyVNC2SWF) slows to a crawl when XDesktopWaves is turned on.

Some notes:
1) I am using Fluxbox and no GTK themeing or anything because PyVNC2SWF crashes using Dapper's version of PyGame, so I have created a basic Breezy installation in a chroot and done it from there (I would normally use X11VNC on my Dapper system, then run PyVNC2SWF in the Breezy system to capture it, but this time there was no need)
2) Don't bother telling me that the Stargate symbols get screwed up or anything petty like that, it is just a demonstration and if you do it yourself then you can spend more time on it and use a better starting image, etc.
3) Yes I am logged in as root, but that is because my Breezy chroot doesn't actually have any other users
4) This WILL NOT work with a Composite enabled X server, that means XGL is right out, and any Xorg or AiGLX with the Composite section enabled in their xorg.conf (AiGLX uses this for Compiz, so it is usually on if you are using AiGLX with Compiz). This is because XTeddy just ends up drawing a completely white window in the shape of the image, instead of drawing the image. I have filed a bug here: [https://launchpad.net/distros/ubuntu/+source/xteddy/+bug/57783](https://launchpad.net/distros/ubuntu/+source/xteddy/+bug/57783)
5) If you want to use this as your background then try putting the "-wm" option on XTeddy, then your Window Manager should be able to manipulate it. I use Enlightenment 0.16 and this works fine, letting me set the window to Borderless and it's stacking layer to Below.

Have fun!

---

### Post by DarkN00b on 2007-11-04
Excellent tut. I only wish I could have seen the final result. Does this only work on Fluxbox?

OOps, no compositing. Right out for me then; I'm using Compiz-fusion. Still pretty cool though.

---

