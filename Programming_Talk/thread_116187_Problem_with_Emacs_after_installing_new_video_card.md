---
title: "Problem with Emacs after installing new video card..."
date: 2006-01-12
forum: Programming Talk
---

### Post by mmcmonster on 2006-01-12
I just installed a new video card and ran 'sudo dpkg-reconfigure xserver-xorg' to get things up and running.

Now, when I run emacs, I get the following errors:
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

Also, my emacs window comes up with a lot of squares taking the place of the characters. I'm pretty sure I need to re-create the X fonts, but have no idea how to do it. I tried doing a re-install of emacs and a few components of X via synaptic, and then did a reboot of the entire OS, with no effect. Any ideas?

Or am I completely off base?

BTW, emacs was working perfectly before the video card upgrade, and still works perfectly if I login in text mode (tty1).

(I cross-posted this to the video hardware forum, but haven't got any responses there. :-( )

---

### Post by mmcmonster on 2006-01-12
Never mind.

I re-ran 'sudo dpkg-reconfigure xserver-xorg' and all is well. :-)

---

