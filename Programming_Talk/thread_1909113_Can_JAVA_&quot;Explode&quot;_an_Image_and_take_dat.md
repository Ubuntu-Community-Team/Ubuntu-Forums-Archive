---
title: "Can JAVA &quot;Explode&quot; an Image and take data from it?"
date: 2012-01-14
forum: Programming Talk
---

### Post by Lucradia on 2012-01-14
HTML / CSS has a screen function that allows a PNG image to be broken into many images and placed around the layout of a page. Java can do this too I'm sure, but what I'm specifically asking is, if Java can do this, and interpret a part of the image as ascii / dec code and translate that part into a global variable used to check something within the code.

Exa, if I make let's say this image:

[img]http://i.imgur.com/xxgJ1.png[/img]

Note the upper far right. Using the below reference:

[img]http://i.imgur.com/G1RbV.png[/img]

You get this:

7010110997108101

Which, if [translated from ASCII / DEC]("http://home.paulschou.net/tools/xlate/"), gives you "Female" as a string. The image will only have that amount of pixels dedicated (maximum) to the ASCII however, since the other String I want to compare is "Male" and has less ASCII / DEC numbers.

So again, is this possible? Or is there some other way I can use JAVA to parse Male / female from pixels in an image?

---

### Post by undecim on 2012-01-14
Well of course. You can encode 3 bytes of data in a pixel, as long as you're using lossless formats. In fact, this is something that Evercookie (presumably using javascript) does with the browser cache to track users. Then there's also the various flavors of barcodes... The benefit to those is that you can store them in lossy formats without losing the barcode data.

I know that there are ways to read individual pixels in Javascript, but unfortunately I don't have any snippets to share.

Though it would certainly be more efficient to store it in a plaintext file, if less interesting

---

### Post by Lucradia on 2012-01-14
> **undecim said:**
> Though it would certainly be more efficient to store it in a plaintext file, if less interesting

I have to use lossy / no text files (PNG actually, specifically) since it's going to be part of a mod for Minecraft to allow the game to recognize if a user is male or female, and use different sounds and skin image dependant on this if/else check.

---

### Post by lisati on 2012-01-14
*Thread moved to **Programming Talk**.*

---

### Post by undecim on 2012-01-14
> **Lucradia said:**
> I have to use lossy / no text files (PNG actually, specifically) since it's going to be part of a mod for Minecraft to allow the game to recognize if a user is male or female, and use different sounds and skin image dependant on this if/else check.

PNG is lossless (assuming that Minecraft doesn't do anything special with the image), so you can just store pixels that aren't used (for example, that extend outside of the viewed part of the image, like the bottom 20 pixels of a 100x100 png as the background of a 100x80 element on a webpage).

For loading the pixel data, check out [http://www.exampledepot.com/egs/java.awt.image/imagepixel.html](http://www.exampledepot.com/egs/java.awt.image/imagepixel.html)

Get the RGB values of the pixel, and typecast each to a char.

---

### Post by Lucradia on 2012-01-14
> **undecim said:**
> PNG is lossless (assuming that Minecraft doesn't do anything special with the image), so you can just store pixels that aren't used (for example, that extend outside of the viewed part of the image, like the bottom 20 pixels of a 100x100 png as the background of a 100x80 element on a webpage).

For loading the pixel data, check out [http://www.exampledepot.com/egs/java.awt.image/imagepixel.html](http://www.exampledepot.com/egs/java.awt.image/imagepixel.html)

Get the RGB values of the pixel, and typecast each to a char.

I can't put the pixels outside the image, so the image MUST stay 64 x 32 (width x height)

You can see what pixels are used where: [http://www.minershoes.com/](http://www.minershoes.com/)

However, your link doesn't quarantine an area then only get an "Area" (IE: 3x3) instead, only getting one pixel?

---

