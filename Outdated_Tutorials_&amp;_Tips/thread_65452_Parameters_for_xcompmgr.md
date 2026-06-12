---
title: "Parameters for xcompmgr"
date: 2005-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by vayu on 2005-09-14
I found the parameters for xcompmgr:

[http://blogs.linux.ie/frankly/2004/09/29/xcompmgr-options/](http://blogs.linux.ie/frankly/2004/09/29/xcompmgr-options/) 

xcompmgr options

Many people are playing with xorg 6.8.1 and the xcompmgr application. Unfortunately, it seems rare (currently) for the xcompmgr options to be documented. So here they are in full:

I tend to use “xcompmgr -cfC &”, but it’s up to you what you want to play with !

xcompmgr v1.0
usage: xcompmgr [options]
Options
-d display Specifies which display should be managed.
-r radius Specifies the blur radius for client-side shadows. (default 12)
-o opacity Specifies the translucency for client-side shadows. (default .75)
-l left-offset Specifies the left offset for client-side shadows. (default -15)
-t top-offset Specifies the top offset for clinet-side shadows. (default -15)
-I fade-in-step Specifies the opacity change between steps while fading in. (default 0.028 )
-O fade-out-step Specifies the opacity change between steps while fading out. (default 0.03)
-D fade-delta-time Specifies the time between steps in a fade in milliseconds. (default 10)
-a Use automatic server-side compositing. Faster, but no special effects.
-c Draw client-side shadows with fuzzy edges.
-C Avoid drawing shadows on dock/panel windows.
-f Fade windows in/out when opening/closing.
-F Fade windows during opacity changes.
-n Normal client-side compositing with transparency support
-s Draw server-side shadows with sharp edges.
-S Enable synchronous operation (for debugging).

---

