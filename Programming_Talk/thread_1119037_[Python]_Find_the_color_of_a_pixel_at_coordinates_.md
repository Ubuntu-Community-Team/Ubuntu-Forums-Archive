---
title: "[Python] Find the color of a pixel at coordinates (X,Y)"
date: 2009-04-07
forum: Programming Talk
---

### Post by JamesWP on 2009-04-07
Hi there, I've done a fair bit of searching but haven't been able to find anything, is there a way (preferably one with a light memory footprint) to grab the color (in RGB format or w/e.) of a pixel on the screen, at say coordinates 10,10?

---

### Post by JamesWP on 2009-04-09
Bump!

I've done a bit of searching, and came up with a few ideas, anyone care to expand on any of them?

Taking a screenshot of the screen, then finding the color of the pixel from there, this would be too slow though I imagine, unless there's a way of taking a screenshot of a single pixel of the screen?

I've heard that python-xlib has a function called XGetImage, but can't really find anything about it, could this suit my purpose?

For windows machines, you can use some win32 api and get the WindowDC and do it all that way, but I can't find anything similar with linux? :-s

If it's going to be too much effort to write my own, are there any lightweight terminal apps that work like gcolor2, but you supply coordinates instead of clicking with the mouse?

Thanks!

---

### Post by soltanis on 2009-04-09
Unfortunately I know very little about Xorg programming, however I can offer you this:

[http://www.manpagez.com/man/3/XGetPixel/](http://www.manpagez.com/man/3/XGetPixel/)

It seems like you can only do this from an XImage. There might be a function to turn your screen into an XImage, but I'm not sure how much better of a solution this is than taking a screenshot and then doing what you said. Perhaps because it's using X functions it won't take as long (won't have to convert between formats) but would probably still be very slow.

---

### Post by vambo on 2009-04-09
Have look at the pygtk docs ([http://www.pygtk.org/docs/pygtk/index.html]("http://www.pygtk.org/docs/pygtk/index.html")) - gtk.gdk.Screen has a set of methods that might help you achieve what you're after.
Never had to get this close to the electrons myself :), so I can't give an opinion.

---

### Post by lavinog on 2009-05-21
what about taking a screenshot and getting the pixel value from the image?

---

### Post by Perkins on 2009-09-21
I was just looking for this myself.  I can't find anything to do it directly, but the programs grabc and xdotool from the repository can probably get you there.  grabc grabs the colour values from a location on the screen where you click the mouse, and xdotool can be used to tell the mouse to click on a particular place.

---

### Post by Marco A on 2009-09-22
.

---

