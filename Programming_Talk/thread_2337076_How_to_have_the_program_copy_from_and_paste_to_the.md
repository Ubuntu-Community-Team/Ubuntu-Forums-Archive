---
title: "How to have the program copy from and paste to the clipboard? In C++"
date: 2016-09-14
forum: Programming Talk
---

### Post by Oinos on 2016-09-14
I'm on Ubuntu 14.04, Codeblocks 13.12, c++14. I have long searched the internet and this forum to no avail. The only thig I've discovered is that clipboards on Linux are mess in general and some code exclusive to Qt.
Thanks in advance.

---

### Post by TheFu on 2016-09-14
Which clipboard?  

I don't know **anything** about codeblocks.  I've used vi/vim plus 3 xterms for my IDE the last 15 yrs.  Does codeblocks prevent the x-buffer from working?

If you program using X/Windows (Xm, Xt, xlib), the x-buffer is there and automatically available for select/paste. A programmer has to go out of his way to prevent this from working.  The widget layers automatically pass the message around as needed and the WM controls it for the "select" and the "paste" parts.

So - if it doesn't work on stock 14.04 running Unity, try a different WM.  Load openbox and try it there.  I haven't touched Unity since 12.04 - purged it back then.

OTOH, if you use some funky toolkit that blocks the x-buffer, then you need to use whatever method that toolkit/library requires. It depends on the library being used.  I can say that on 16.04 running openbox, the x-buffer is working fine and I remember it working fine for most normal programs created

---

### Post by Oinos on 2016-09-14
I should've said I'm not very acquainted with Ubuntu and Linux in general. How do I access that x-buffer? No search seems to return anything relevant. I'm making a console application.

---

### Post by TheFu on 2016-09-14
If you don't run X/Windows (i.e. any GUI), then you can't use the x-buffer.  Select/paste text inside a console app is something I handle by running inside an xterm. This provides a GUI and X/Windows.  Actually, this is why I much prefer xterms over the fancy terminals that seem to be the default these days.

Perhaps some quick background about X/Windows is needed?  [https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System) ... explains the Client/Server architecture and, from a high level, the different parts. Key things to understand is that X/Windows is a networked protocol with a client and a server. The server runs on the physical machine you sit behind and the client can run on any machine in the world - accessable via a network.  This is backwards of most C/S architectures.  Next to understand is that programs need a window manager to control them and their view.  The window decoration is from the WM, not the program.  Based on the current focus, x-events are sent to the different parts of the screen/layers ... starting from the total window, inside the program with focus, down to the specific "widget" to handle the action (like a "select").  If that widget doesn't understand what to do with the x-event, then its parent handles it, up the chain. It is a hierarchy.  Anyway, that article should explain it better than I.

---

