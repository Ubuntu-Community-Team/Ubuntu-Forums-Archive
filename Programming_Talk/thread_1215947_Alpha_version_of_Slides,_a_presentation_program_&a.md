---
title: "Alpha version of Slides, a presentation program &amp; alternative to OpenOffice.org Impre"
date: 2009-07-17
forum: Programming Talk
---

### Post by tom66 on 2009-07-17
Well I was working on a presentation program a while back, and I kind of gave up on it due to several problems with the original Python version:

 - It was slow to move objects because EVERYTHING had to be redrawn.
 - Complex things like text which use Cairo a lot became sluggish with any more than 50 words.
 - Coordinates were completely screwed up. Path editing was impossible, as far as I could see.
 - I'd just started with Python so the code was quite messy. 

Now originally I thought Cairo was the problem. Cairo produces beautiful graphics, but at a cost of performance loss. Luckily, I soon discovered I was wrong: though Cairo is slower than a basic drawing library, the features it offers, written in C, are faster than what I could write in Python. I could completely avoid them, but then I would be missing out on some very cool features that few, if any, presentation programs have.

So I started from scratch. I made a plan:

 - All fills are cached. They're only recalculated when a change is made, e.g. changing a stop colour for gradients.
 - All objects are first drawn to a pattern and then cached. They're only recalculated when a change is made, just like fills. 
 - Objects are recalculated on zoom changes.
 - Object patterns are redrawn when the screen needs to be changed.
 - When I implement object movement, I will do it by taking a copy of the canvas without the object, drawing the object on the canvas, and moving it around. No extreme refreshing of the screen is necessary. 
 - For text and other elements, Pango markup will be cached, as will the patterns and paths.
 - Graphs and other complex shapes will also be cached.
 - Coordinates are now absolute, at 100% the pixels are exact. On the old version they ranged from 0.0 to 1.0 which meant a lot of messy code for figuring out click positions, etc.

Anyway, I've got the most basic rendering engine working. But it's got a few bugs:

 - Stroke seems to be stuck inside the objects but sometimes leaves the objects. This is caused by incorrect stroke clipping rectangles (given by Cairo, but I'm not sure if there's another bug elsewhere putting incorrect info in). 
 - Scrolling at high zoom amounts can cause flickering. This is due to how the redrawing works. It would be best to avoid this, but it might not be possible.
 - Zooming to 200% shows some objects mysteriously clipped. I believe this is due to Cairo clipping the objects when they get out of range, but I'm not entirely sure. 
 - Sometimes, the slide.kill() function isn't executed. This function erases the temporary files used to create thumbnails. I've got to figure out why, if the application abnormally terminates by Ctrl-C, it doesn't always get executed, despite being put in an try...except handler for KeyboardInterrupt. However, normal quit methods DO always clean up properly. 

Also some features need to be implemented. It's just a basic rendering engine at the moment.

 - You can't manipulate objects.
 - Text objects aren't implemented.
 - Slides can't yet be created, moved or deleted.

I've included a .tar.gz so you can check it out but don't expect much.

---

### Post by Can+~ on 2009-07-17
Very nice, at least the basic idea works well.

To fix problem #2. Are you sure you need to redraw everything inside the Drawing area when scrolling? I would thing that GTK would automatically displace the content inside just like it would do with a normal image.

---

### Post by tom66 on 2009-07-17
I've implemented scrolling myself, GTK just sees a DrawingArea and some scrollbars. Whilst I considered the idea of using a gtk.ScrolledWindow, it would cause a few problems, namely, a large amount of memory consumption when having a high zoom level, but also sluggish zoom as everything would need to be redrawn when a zoom action was requested. It's better, I believe, to split the redrawing over several scroll actions, that way, the user gets a seemingly more responsive application. Also, adding offset parameters for scrolling allows me to do interesting effects which would be otherwise impossible.

---

### Post by BluShift on 2009-07-17
Wow. That's all I can say. I can see how the current code doesn't let a whole lot be done, but ALREADY this is looking very very promising. I'm still learning to script in python... I am very envious of your skill :D

Although I'm sure I could not contribute much, if you'd like help I can totally jump ship :P

---

### Post by tom66 on 2009-07-18
Thanks guys.

I think I should get the basics working soon, like object and text editing. Then it would be ready for a version 0.1 release.

---

### Post by hessiess on 2009-07-18
Looks interesting, do you intend to alow working with odp files, possibly as the native format? doing so would give instant boost to the programs usability, as using a custom viewer would be un-necessary.

---

### Post by tom66 on 2009-07-18
Initially, Slides will require its own file formats for the advanced features it offers. However, I'm sure there's a way to develop it so odp export is a possible idea, as well as MS Office PowerPoint. And because Cairo supports PNG and PDF output then I will also implement this.

---

### Post by tom66 on 2009-07-20
If anyone wants to see what's been done since I've been gone, the following changes have been made:
 - You can select objects.
 - You can move objects. It's not slow either.
 - Thumbnails update when you make a change. 
 - There is no flickering when scrolling; I fixed that; it was updating all of the caches every time you scrolled.

Enjoy!

---

