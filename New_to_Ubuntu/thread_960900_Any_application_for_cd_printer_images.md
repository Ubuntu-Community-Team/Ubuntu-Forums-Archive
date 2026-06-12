---
title: "Any application for cd printer images?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Nonno Bassotto on 2008-10-27
Is there any application available for Linux to produce an image suitable to be printed on a cd? I guess I just have to make a circular png with a hole or something like that, but I'm not sure, and then i don't know the size and so on. Any owner of a cd printer can illuminate me?

---

### Post by ashmew2 on 2008-10-28
Try GCover : [http://gcover.sourceforge.net/](http://gcover.sourceforge.net/)

-OR-

Nero Linux 3 : [http://www.nero.com/ena/linux3.html](http://www.nero.com/ena/linux3.html)

---

### Post by Nonno Bassotto on 2008-10-28
I don't need to create a cover page. I'm talking about the image that gets printed on the cd itself.

---

### Post by indytim on 2008-10-28
Try GIMP.  Steep learning curve but (in my opinion) well worth the effort.

IndyTim

---

### Post by Zimmer on 2008-10-28
openoffice labels !
J8676  size, if I remember correctly. It is a couple of years since I produced a label.
EDIT:
Remembered how I did it now. Used Openoffice presentation , created 11.7cm elipses (circles) and constructed the labels on the circle. Grouped the resulting image and copied and pasted that into the label template for printing.

I can't quite remember how I squeezed rectangular images into the circle format , but when I do I will get back to you.
EDIT2
Ok, create the elipse/circle. Right click >Area   Set Area Fill to Bitmap. Select the tab <Bitmaps> and import your image.
Select the <Area> tab and select the new image from the list. Uncheck the  <tile> option on the right to 'fit ' the image to the circle.
That's the basics.  You will need to experiment with your image sizes, tiling etc. to achieve whatever effect you require.

Add any other text boxes etc. to the elipse and group when finished. 
To produce a printed label you will need to create a label in the required size as mentioned in the beginning and copy and paste your grouped object into it.

---

### Post by NoVista on 2008-10-28
Lightscribe:
[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)
[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

Linux.com did a good overview article a while back at:
[http://www.linux.com/feature/118705](http://www.linux.com/feature/118705)

---

### Post by philinux on 2008-10-28
IIRC glabels can do it. It's in synaptic.

If it's not that then kover does it.

---

### Post by Nonno Bassotto on 2008-10-28
I'll try lightscribe and glabels. GIMP is not the way to go. I know how to use it, but the whole point is that I want to be sure to create a standard image which can be readily used by CD printers (I don't have one).

---

