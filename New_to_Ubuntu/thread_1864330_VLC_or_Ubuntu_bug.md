---
title: "VLC or Ubuntu bug?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-18
When you try to open a .m3u file you get a window like this:

[IMG]http://i.imgur.com/UwWAL.png[/IMG]

.m3u is a media streaming extension and I have saved VLC as the default player but I get it every time I double click on the file :???: I have to hit display as if it were a text file to get it to play in VLC...I think this is a Ubuntu window, no? Where should I report it?

---

### Post by ron999 on 2011-10-18
What about...
Right-click...
Open with...
VLC...
Set selected application as default action of this type...

---

### Post by Dr. C on 2011-10-18
[This]("http://ubuntuforums.org/showthread.php?t=1093166") thread might also help. where did the m3u file come from?

---

### Post by d4m1r on 2011-10-18
> **ron999 said:**
> What about...
Right-click...
Open with...
VLC...
Set selected application as default action of this type...


It already is set as the default.

@Dr C, I downloaded it from a site. On my Windows partition I set VLC as the default program for .m3u files and double clicking on it opens it up automatically with VLC..

---

### Post by d4m1r on 2011-10-18
> **Dr. C said:**
> [This]("http://ubuntuforums.org/showthread.php?t=1093166") thread might also help. where did the m3u file come from?

Thanks for the link, I was at least able to make a workaround. If you have a .m3u file, open it in a text editor and edit it like this:

[playlist] 
NumberOfEntries=1 
File1=http://addresshere

Save it, and rename the extension to .pls. Now VLC will automatically open it and play\\:D/

---

