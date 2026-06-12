---
title: "How do you make an image background transparent?"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by corncob on 2012-01-16
Does anyone know how to make the background on an image transparent?  I'll try to attach the specific picture: [IMG]http://uppix.net/4/a/f/0b2189c581eccb228da8eb31c83f1.jpg[/IMG]
It looks transparent here because its on a white background.

---

### Post by gandaran on 2012-01-16
gimp can make any color transparent or just the white background which is very simple to do, google search how to do it with gimp.

---

### Post by mcduck on 2012-01-16
...the problem here, though, is that making a single color transparent isn't enough in every situation. The image in question has some antialiasing which requires you to find a balance with how much of the white shades to make transparent without loosing some of the image itself.

..and to make things even more annoying, the shadows under the letters should probably be made partially transparent to fit whatever background the image is used with. And there is no simple way to do that kind of things.

I'd probably use the Select/By Color tool in Gimp with a bit of tweaking with the Treshold to select the white background and remove it, and then the same method to select the shadows, move them to another layer, and then make the layer the desired transparency. 

It's not impossible, or particularly hard, but you'll need some image editing skills and a bit of manual work to do that, so don't expect any single-click solution.

(..and keep in mind that to actually keep the transparency in the image, you need to save it as a file type that supports transparency. Since the image in question requires full alpha channel transparency as opposed to a single transparent color, I'd recommend PNG format.)

Edit: I case you'd happen to have the font used and the small image from the bottom left corner available, it would most likely be less work to just redo the image with the transparent background...

---

### Post by SeijiSensei on 2012-01-16
Here's a rough-and-ready version from GIMP.  I opened the image, added an alpha channel (Layer > Transparency > Add Alpha Channel), chose "Select by Color" and clicked on the white background.  As mcduck observes, the shadows, etc., are left untouched while the pure white pixels are made transparent.
[IMG]http://www.takinganimeseriously.com/images/trans2.jpg[/IMG]

I saved the image as a JPEG.  GIMP will complain that the JPEG format doesn't support layers, so just choose the "flatten" option when asked.

---

### Post by mcduck on 2012-01-16
...and here's one with transparent shadows as well... ;)

---

### Post by corncob on 2012-01-17
> **mcduck said:**
> ...and here's one with transparent shadows as well... ;)

Thanks guys and gals!  crug.png was exactly what the president of the club was looking for.  I'll mark the thread as solved although I see where it takes a lot of know-how to do.

---

