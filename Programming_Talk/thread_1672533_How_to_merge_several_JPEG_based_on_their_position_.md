---
title: "How to merge several JPEG based on their position X and Y ?"
date: 2011-01-21
forum: Programming Talk
---

### Post by honeybear on 2011-01-21
file1_0_0.jpg
file2_100_100.jpg
file3_0_100.jpg
...

and all is building a single JPG made of several based on their position X adn Y? 


Thank you in advance!
Cheers

---

### Post by PaulM1985 on 2011-01-21
In Java you could create a BufferedImage the size of the total image.

Then get the Graphics for the total image and paint each of the images in your folder based on the X and Y value.

Each of the little images can be read using ImageIO.read() and you could parse the file names of the little images to get the X and Y.

Paul

---

### Post by worksofcraft on 2011-01-22
> **honeybear said:**
> file1_0_0.jpg
file2_100_100.jpg
file3_0_100.jpg
...

and all is building a single JPG made of several based on their position X adn Y? 


Thank you in advance!
Cheers

I happen to be writing a tutorial for how to use [libjpeg]("http://www.ijg.org/") with the [AGG graphics library]("http://www.antigrain.com/") and it would be really cool if you could explain a bit more about what you are trying to do because it might make a really good example program... and I might be able to help you out here too :)

So like... you have bunch of jpeg files and you want to combine them to make a bigger picture?

How do you determine their position in the big picture?

Do you envisage having overlap and what would happen at the intersections?

What would you do with empty spaces?

---

### Post by LemursDontExist on 2011-02-09
Assuming you want to do this programatically, I'd check out [imagemagick]("http://www.imagemagick.org/script/index.php").  Specifically the [montage]("http://www.imagemagick.org/script/montage.php?ImageMagick=9ssrnq7bkgmk396098p1a9s7j3") command.  There is a command line version of imagemagick as well as several language bindings available.

---

