---
title: "HOWTO: Custom Image for your Applications bar (replace gnome foot)"
date: 2005-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by derrick1985 on 2005-06-27
Hey all

This HOWTO is inspired by demon666_nl's HOWTO on changing the gnome-foot to the Ubuntu logo, i'm just taking it up a notch and showing howto change it to anything you want. [http://www.ubuntuforums.org/showthread.php?t=26854](http://www.ubuntuforums.org/showthread.php?t=26854)

Things you will need:

1. The image you want to be replaced by the gnome-foot. The squarer the image is, the better, and you will see why when we have to resize it. 

2. GIMP (or any other image munipulation program that can handle transparency.

3. Patience. Sometimes it may take a while to get your image the way you like it, in terms of getting the transparency right. Usually, if the background is white, and there is no other white in the picture, you would make the white transparent and all would be ok. Get it?

First off, we need to take our image and resize it. I got my image from google image search, but you can get it from anywheres you want. Open it in gimp and select Image---Scale image.

The gnome foot is a 24x24 image, so we need to scale our image down to as close to these dimensions as possible (that's why square'er, the better). Enter in 24 in the width box and hit the chain beside it. It should scale down your height too.  so, my image ended up being 24x23, and that works great.

Now, we need to add a transparency, this way, if we ever change our menu bar's background colour, the colour of the image will change too. Go Layer---Transparency---Add alpha channel. Now, go back into Layer---Transparency---Colour to Alpha. Choose the colour you want to be transparent (usually the background colour).

Now, we need to save the image. Go File---Save As and from the new window, choose Select File Type (by extension) and choose .png from the list. Save your file as any name, in your home folder.

Now, we need to get that image into the right directory, and rename it to the proper name.

From a terminal, type:

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

That command backs up our current Gnome-Foot image.

sudo cp /home/yourusername/your_image_name.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

There, now our image is moved, in it's proper place, and ready to be used. Now, lets reload our Gnome-panels to see our new image.

killall gnome-panel

voila, custom menubar image.

Hope you all like.

Screenshot below to show you what my finished project ended up looking like.

---

### Post by krdp on 2005-06-27
Wow nice HOWTO thanks so much :)

---

