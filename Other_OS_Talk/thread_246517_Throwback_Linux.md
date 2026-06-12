---
title: "Throwback Linux"
date: 2006-08-29
forum: Other OS Talk
---

### Post by justin whitaker on 2006-08-29
I've been tossing around an idea that I am calling Throwback Linux. Here's what it would be like:

[LIST]
[*]Whereever possible, a console tool would be used
[*]A light keyboard based wm like wmii or ion would be available for everything else
[*]It would be desktop centric, not server centric
[*]It would make use of cool apps like bashburn, pytone, etc.
[*]It would include performance patches like the CK patch
[*]It would be an installable live CD[/LIST]

Sort of like grml, without all the cruft and clutter. Based on Ubuntu, of course, because, let's face it, Ubuntu rocks. :mrgreen: 

Thoughts? Ideas? Interest?

---

### Post by 3rdalbum on 2006-08-29
You wanna know something crazy? For a month or so I've been thinking how great a text-based desktop distro would be. You could have Links2 for browsing direct to framebuffer, MPlay as the textual frontend for MPlayer, some kind of text-based word processor, ImageMagick for image editing, that console-based IRC client for chat, ivman for automounting, and the user's shell could be Fish. (I'm a big Fish fan if you haven't already noticed)

Completely text-based, but with simple interactive configuration programs. No X11 at all.

I just thought that it could be a set of scripts that you could install on top of Ubuntu Server. I had also considered remastering a business-card Live CD like DSL or Austrumi.

You might want to head over to the Puppy Linux website and check out OneBone Puppy. If you have programming experience I'm sure they'd love to have you onboard, but I think their aims are more similar to mine than they are to yours.

P.S. I call mine "Text Pistols"... yes, I did steal that from an article.

---

### Post by justin whitaker on 2006-08-29
> **3rdalbum said:**
> You wanna know something crazy? For a month or so I've been thinking how great a text-based desktop distro would be. You could have Links2 for browsing direct to framebuffer, MPlay as the textual frontend for MPlayer, some kind of text-based word processor, ImageMagick for image editing, that console-based IRC client for chat, ivman for automounting, and the user's shell could be Fish. (I'm a big Fish fan if you haven't already noticed)

Completely text-based, but with simple interactive configuration programs. No X11 at all.

I just thought that it could be a set of scripts that you could install on top of Ubuntu Server. I had also considered remastering a business-card Live CD like DSL or Austrumi.

You might want to head over to the Puppy Linux website and check out OneBone Puppy. If you have programming experience I'm sure they'd love to have you onboard, but I think their aims are more similar to mine than they are to yours.

P.S. I call mine "Text Pistols"... yes, I did steal that from an article.


Well, when I was thinking about it, the one area where a text based distro would really fall flat would be in graphics manipulation. 

You could use screen to multiplex a terminal, so you could have tons of apps running without X. 

I have little experience with Imagemagik (although I recognize it would have to be installed), so to get GIMP running, I would need some minimal wm. 

WMII was my first choice, since you could use alot of the keyboard commands to manipulate the desktop on the fly. WMII has another benefit in that you could arrange columns of terminals on a single desktop, instead of switching screens, which means you could have a root prompt, htop, bashburn, etc. links2, and more on a single desk(Ion does this as well).

There are very few word processors left for console, although vim and/or emacs can be used quite happily. 

I like the idea of an installer script on top of a server install. Thanks!8)

---

