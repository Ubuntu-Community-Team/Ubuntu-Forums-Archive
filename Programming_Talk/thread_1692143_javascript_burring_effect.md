---
title: "javascript burring effect"
date: 2011-02-21
forum: Programming Talk
---

### Post by Finalfantasykid on 2011-02-21
I am wondering if this is possible.

I have a semi-transparent div element, but I am having a hard time figuring out how to make things which are behind it semi transparent(like windows aero effects).

Any google search I do shows how to blur images, but none seem to explain how I would do this, so I am wondering if it is even possible.  I don't know much javascript, so be nice :)

---

### Post by ve4cib on 2011-02-21
No, I don't think there's any way of making everything on the page semi-transparent to the point where you can see your desktop wallpaper.  Browsers just won't let you do that.

You'll always have some background layer of the webpage that will be opaque.  But you can have all of your elements that float above that background layer be semi-transparent by setting their backgrounds to something like "background-color: rgba(255,255,255,0.7);" in your CSS.

Depending on what exactly you need, [extJS](http://dev.sencha.com/deploy/dev/docs/) has some very nice widgets and such for web applications.  Some of the themes to use semi-transparent window borders on the floating panels, and do some nifty opacity changes while dragging.

---

### Post by Finalfantasykid on 2011-02-21
Ok I didn't explain it properly.  I have this graph which looks something like this:

[http://img828.imageshack.us/i/screenshot6ra.png/](http://img828.imageshack.us/i/screenshot6ra.png/)

I would like the nodes to blur everything behind them.

---

### Post by ve4cib on 2011-02-21
I'm not seeing any blurring going on in that picture.  There's a halo and a semi-opaque layer in front of one element, but the edges of the element in the back are still crisp.  I'm still lost as to what you're after.  Do you want fuzzy (blurred) images, or do you want what's in that picture?

---

### Post by Finalfantasykid on 2011-02-21
That picture is what I have going on right now(there is no blurring).  I would like there to be blurring behind each node, if that is possible.

---

### Post by ve4cib on 2011-02-22
Ah... okay, I get it now.

Short answer: no, I don't think that's possible to do in JS.

The only way I can think of to do it would basically be to reimplement the entire browser in JS, and render everything to a canvas tag.  Then you could implement the blurring yourself.  But -- and you've probably figured this out already -- that's a really, REALLY stupid idea.

Browsers can be thought of in very general terms as a tiling window manager.  Every element stacks neatly over top, obscuring whatever's underneath.  The fact that we have any support at all for transparency is pretty cool.

But to blur everything underneath a particular element you'd basically need a composting layout engine.  And such things, to my knowledge, don't exist.

So if you're stuck working in a browser the best you can do is have a semi-transparent overlay to fade-out whatever's behind.  You can't blur it.

---

### Post by myrtle1908 on 2011-02-22
You could probably pull it off with SVG.  Have a look at the excellent JS SVG lib Raphael.  I use Raphael alot but not for what the OP is doing.  I mainly use it for interactive charts etc.

[http://raphaeljs.com/](http://raphaeljs.com/)

[http://eng.wealthfront.com/2010/11/when-canvas-doesnt-cut-it-raphaeljs.html](http://eng.wealthfront.com/2010/11/when-canvas-doesnt-cut-it-raphaeljs.html)

---

