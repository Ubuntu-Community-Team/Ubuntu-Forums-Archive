---
title: "need advice on image resizer program"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Indy452 on 2008-09-14
Can someone suggest an easy to use image viewer that can resize the image from 2 mb to 256 kbs??  Seems like quite a reduction but I need to resize some images I keep in my pictures folder to this much smaller size so I can post them.

I can't seem to figure gimp out. Too much mumbo jumbo on it for my needs. I need something fairly simple.

Thanks 

Neal

---

### Post by pavel989 on 2008-09-14
within gimp. you should simply open them and try to go to save and save it in a more compressed format. or look into f-spot, i think that can do it

---

### Post by Tatty on 2008-09-14
try installing nautilus-image-converter from the repos.

That adds the ability to resize images directly from nautilus.

---

### Post by Indy452 on 2008-09-14
What do you all think of gthumb?

---

### Post by pavel989 on 2008-09-14
havent used it ina  while

---

### Post by barx on 2008-09-14
You can do that or what I recomend you, only if the image is not very complex use inkscape, with F6 to mark the dots and follow the line and F2 you can modify to fit to the draw or image, you can paint with the color squares of the bottom or right-click on the path and change the color of the line, color of the interior and the line.

this is a good option to get a picture with loseless of pixels, you'll use vectors, that little or big the image will never distorsioned or see ugly.

If you only want to make smaller or bigger an image nommater how it looks, use gimp xP.

---

### Post by unutbu on 2008-09-14
```
sudo apt-get install imagemagick

```
This maintains the pixel width and height, but reduces the quality (more compression)
```
convert -quality 50 picture.jpg picture-resized.jpg
   
```
This resizes the picture by 50% while maintaining the aspect ratio
```
convert -resize 50% picture.jpg picture-resized.jpg

```
This resizes the picture to max width of 800 and max height of 600 while maintaining the aspect ratio:
```
convert -resize 800x600 picture.jpg picture-resized.jpg
```

This resizes the picture to 800x600, ignoring the original aspect ratio:
```
convert -resize 800x600! picture.jpg picture-resized.jpg
```

See [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)
[http://www.imagemagick.org/script/command-line-options.php](http://www.imagemagick.org/script/command-line-options.php)
[http://www.imagemagick.org/www/convert.html](http://www.imagemagick.org/www/convert.html)

---

### Post by the.phantom on 2008-09-14
showfoto ( it's in the add/remove list)

can do all the normal pic stuff, resize/rotate/crop/color correction and such
shows a preview if you want too change the jpg compression

---

