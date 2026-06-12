---
title: "apply patch"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Bristol Rogue on 2008-04-27
I have found someone publishing a solution to a problem I have with gnomeradio, the problem is that involves "applying a patch" and I haven't a clue where to start.

The link to the discussion is:

[http://bugzilla.gnome.org/show_bug.cgi?id=506037](http://bugzilla.gnome.org/show_bug.cgi?id=506037)

and the 'solution' is at comment#4, link below.

[http://bugzilla.gnome.org/attachment.cgi?id=104558&action=view](http://bugzilla.gnome.org/attachment.cgi?id=104558&action=view)

If anyone has the patience to write up an idiot's guide, or can give me a link I would appreciate it.

Thanks in anticipation.

:confused:

---

### Post by furtypajohn on 2011-07-01
Save the contents of the second link as some file (which I'll call fix.patch). Save this file on your desktop for convenience.

Then open a terminal (Accessories -> Terminal) and type the following commands:

```
cd /path/to/gnomeradio-1.7

patch -p0 -i ~/Desktop/fix.patch
```Note: that /path/to/gnomeradio-1.7 is a path on your machine that I do not know. You want to be located in the gnomeradio-1.7 folder prior to running the second command.

If you get any errors when you run the patch command post those and I'll see if I can help further.

Here's this for another reference: [http://jungels.net/articles/diff-patch-ten-minutes.html](http://jungels.net/articles/diff-patch-ten-minutes.html)

---

