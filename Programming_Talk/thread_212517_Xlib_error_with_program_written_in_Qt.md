---
title: "Xlib error with program written in Qt"
date: 2006-07-10
forum: Programming Talk
---

### Post by chichilalescu on 2006-07-10
I wrote a program some time ago, that displayed fractals, and it ran just fine.
I used muParser, an opensource parser of mathematical expressions (check it out on sourceforge if you're interested), and qt (3).
When I wrote it, I was using slackware 10.1, and it worked just as fine on slackware 10.2 (obviously recompiled); I used gcc 3.3 and 3.4.
Now I installed all packages I could think were necessary on ubuntu, and I recompiled my program, this time using gcc4 and gcc3.4.
The program is made up of a thread that computes the fractal, and than sends a signal to the window to paint it. As soon as I start the program, I get two X Errors, that look like those I get with a whole bunch of other programs I installed myself (for instance Kile), and one that looks new ( ScimInputContextPlugin() ).
The window runs fine after these, as if nothing happened, and I start the thread that computes the fractal; it runs, and when it finishes, I suppose that while trying to display, the program sends out the last error (Xlib) and then freezes.
I have no ideea why I get these errors, and I have no ideea why the program won't display the image.
The way the program works is this: it computes the fractal and fills a QImage, then the QImage is painted onto a QPixmap, and then the QPixmap is displayed on the window.
If anyone has any clue, I would be gratefull for any thought. Sorry if this post doesn't belong here, but the program worked on Slackware, so I think this is something to do with ubuntu.

X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
ScimInputContextPlugin()
Xlib: unexpected async reply (sequence 0x1081)!

I attached the program source, in case anyone feels like trying.

---

### Post by chichilalescu on 2006-07-15
hello again.

I searched the net, and I found [http://www.faqs.org/faqs/x-faq/part7/section-15.html](http://www.faqs.org/faqs/x-faq/part7/section-15.html) , where it sais "You'll typically get these errors if you are writing a multi-threaded
application and are making X calls from more than one thread".
So I'm sorry, this is not something to do with ubuntu (it's just strange that it worked in slackware and it doesn't work in ubuntu).

---

### Post by chichilalescu on 2006-07-15
I fixed the program, by placing the event that calls for repaint() in the main thread, and it doesn't freeze anymore.

---

