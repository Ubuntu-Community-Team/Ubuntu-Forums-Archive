---
title: "100% div height + header problem."
date: 2012-10-04
forum: Programming Talk
---

### Post by sandyd on 2012-10-04
When I restarted the design of my site, I added a fixed header that scrolled down with the page.

However, it is currently turning out to be (quite) the nightmare. I wanted to create snappable divs (scroll section by section using jquery), so I set the height of each panel to 100%.

Of course, the floating header took up space as well (66px+2px border), so I was forced to use negative margins to make sure that the stuff did not get hidden under the header, and instead have a height equal to the space between the end of the header and the browser window. The divs now overlap, which is not a problem, as I am setting a solid background later on. Now, everything worked, and each slide fit perfectly between the header and the bottom of the screen.

It worked quite well, until I added the slider.

Take a look: [http://dev.sandyd.me/~sandyd/](http://dev.sandyd.me/~sandyd/)

The slider refuses to stay within the div, and starts overlapping the next section.

Any ideas? 
Note that I could force the height to 80% or something by using
```

.dwuserEasyRotator {
	height: 80% !important;

}

```, but I would prefer something that covers that entire section fluidly (if you resize the page right now, each of the sections will still fit between the header and the bottom of the browser window.

---

### Post by juancarlospaco on 2012-10-04
Heres a demo i done for you:

[http://jsfiddle.net/juancarlospaco/4Vwc8/](http://jsfiddle.net/juancarlospaco/4Vwc8/)

Resize the textarea with the mouse, imagine its your slideshow.
A plus..., click title, content will collapse into it.
Theres content outside that box so you can see how flexible it is.

If size/position is hardcoded into JQuery nothing you can do from CSS.

:)

---

### Post by sandyd on 2012-10-04
> **juancarlospaco said:**
> Heres a demo i done for you:

[http://jsfiddle.net/juancarlospaco/4Vwc8/](http://jsfiddle.net/juancarlospaco/4Vwc8/)

Resize the textarea with the mouse, imagine its your slideshow.
A plus..., click title, content will collapse into it.
Theres content outside that box so you can see how flexible it is.

If size/position is hardcoded into JQuery nothing you can do from CSS.

:)
Hmm

It (unfortunately) has the problem of not filling the height properly when resized :(.

---

