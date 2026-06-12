---
title: "Su, sudo or gksu command line"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by aaron36 on 2014-04-16
I need a command to allow me past the "grub" can't find error.... Minimal BASH-like line editing is supported. "TAB" lists.
using GNU GRUB version 2.00-13ubuntu3. Trying to get the video to open on an older "Toshiba" laptop. With a "Trident" onboard graphics card... It seems to want to run. I found older command lines. Any suggestions? And please don't tell me to 
use an earlier version like open suze... I have some unix line knowledge understanding....   Thanks...

---

### Post by Dreamer Fithp Apprentice on 2014-04-16
Maybe I don't understand but that sounds like a booting problem, not a video problem. Maybe it's not the error message I'm assuming it is but one that starts off the same way. So possibly you should quote the whole thing. If it is what it seems to me from what you said, I've had good luck with this:
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)                     

If you mean you want to know how to use the grub command line, doesn't it say something like "type help for help", not exactly, but something similar? You can probably find some documentation here:
[http://www.gnu.org/software/grub/grub-documentation.html](http://www.gnu.org/software/grub/grub-documentation.html)

If this doesn't help, you might want to think about editing your thread title to something more suggestive of what your subject actually is, maybe "stuck at grub prompt".

---

### Post by jbaerboc on 2014-04-16
Yeah I'm not quite sure what you're after here either. It sounds like you are having issues with booting through GRUB, but that wouldn't really have anything to do with your video card. For example if I were to bork my x.org file [video card stuff] and restart my computer it would get past GRUB fine but would fail to load a GUI for Linux and instead would kick me down to a terminal. Is it doing that to you? Is it getting you to a terminal? Or does it not even get passed GRUB boot?

---

