---
title: "Why does the image on this web page look so bad?"
date: 2008-10-10
forum: Programming Talk
---

### Post by tc101 on 2008-10-10
Why does the image on this web page look so bad?  The original is of much higher quality.

[http://katherinedurant.com/](http://katherinedurant.com/)

Is it because I made it smaller using 

<img style="width: 204px; height: 363px;" alt="" src="kdm1.jpg">

Is there some tool in ubuntu that would be a better way to set it to the size I want?

---

### Post by loell on 2008-10-10
yeah, just resize it or crop it in gimp.

oh the reason the image didn't look good, because the page shrink it to your specified width and height.

---

### Post by Sam on 2008-10-10
Open it with "gThumb Image Viewer" there are functions to resize an image.

Or Gimp, which is more advancer than the other... Your choice.

---

### Post by pp. on 2008-10-10
> **tc101 said:**
> Why does the image on this web page look so bad?  The original is of much higher quality.

[http://katherinedurant.com/](http://katherinedurant.com/)

Is it because I made it smaller using 

<img style="width: 204px; height: 363px;" alt="" src="kdm1.jpg">

Is there some tool in ubuntu that would be a better way to set it to the size I want?

You may not realise that you did not, in fact, make the image smaller. You push a largish image through the internet and let the browser reduce its apparent size on the screen. As can be ssen, the browser does not excel at that task.

As the members before me have pointed out, results might be much better if you reduced the image at your end and let the browser just fetch the reduced image at its new 'original' size.

---

### Post by Paul41 on 2008-10-10
> **pp. said:**
> You may not realise that you did not, in fact, make the image smaller. You push a largish image through the internet and let the browser reduce its apparent size on the screen. As can be ssen, the browser does not excel at that task.

As the members before me have pointed out, results might be much better if you reduced the image at your end and let the browser just fetch the reduced image at its new 'original' size.

And as a added bonus the file size would be smaller so the load time would be faster.

---

### Post by Sam on 2008-10-10
Or use both images, a thumbnail which load fast and the high res image when the user clics the thumbnail:

[HTML]<a href="kdm1.jpg"><img style="width: 204px; height: 363px;" alt="" src="kdm1_small.jpg" /></a>[/HTML]

---

### Post by ichekryg on 2008-10-30
Not exactly related to the issue, but...
What is the rational behind AutoRotate (Automatic Orientation)?  I find it quite annoying, to see image in one orientation (nautilus, eye for gnome, fspot, etc), while in reality it could be in totally different orientation. This is especially annoying when you try to attach or upload an image, navigate to a file to just realize that the image is in wrong orientation. 

In Gnome image viewer you can deselect "Automatic Orientation" to show image in original view. Is there the same settings for Nautilus (viewing image thumbnails)?

---

### Post by LaRoza on 2008-10-30
> **ichekryg said:**
> Not exactly related to the issue, but...
What is the rational behind AutoRotate (Automatic Orientation)?  I find it quite annoying, to see image in one orientation (nautilus, eye for gnome, fspot, etc), while in reality it could be in totally different orientation. This is especially annoying when you try to attach or upload an image, navigate to a file to just realize that the image is in wrong orientation. 

In Gnome image viewer you can deselect "Automatic Orientation" to show image in original view. Is there the same settings for Nautilus (viewing image thumbnails)?

Not related to it at all. Please make your own thread in the appropriate forum instead of posting on a random thread in the programming talk forum.

See the Guide to Forum Features link in my sig.

---

