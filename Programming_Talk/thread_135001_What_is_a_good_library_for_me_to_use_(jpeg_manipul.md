---
title: "What is a good library for me to use? (jpeg manipulation)"
date: 2006-02-23
forum: Programming Talk
---

### Post by spaceballl on 2006-02-23
Hi there,

I'm working on a project right now which requires some image manipulation. Specifically, I need to be able to cut images in half and save them as two separate files. Does anyone know if a library that supports this?

I have been looking into libgd. It looks like libgd supports drawing, but no resizing / slicing.

Anyone know of anything? Thanks!

-kevin

---

### Post by hod139 on 2006-02-23
The programs in imagemagick are very good.  You can call them from your program, or you can always download their source and see what they did.

---

### Post by cwaldbieser on 2006-02-23
[QUOTE=spaceballl]Hi there,

I'm working on a project right now which requires some image manipulation. Specifically, I need to be able to cut images in half and save them as two separate files. Does anyone know if a library that supports this?

I have been looking into libgd. It looks like libgd supports drawing, but no resizing / slicing.

Anyone know of anything? Thanks!

-kevin[/QUOTE]

Could you just use the imagemagick tools from a shell script? E.g. convert with the "crop" option used on an image twice to first generate one half and then the other?

---

### Post by spaceballl on 2006-02-23
Well,

it's a big program that will have me recursively cutting the image up into smaller pieces. The program is being written in C so i cant really just use a shell script. Thanks for the imagemagick link. I'll take a look at it, and hopefully it'll be what i'm looking for.

---

### Post by hod139 on 2006-02-23
[quote=spaceballl]Well,

it's a big program that will have me recursively cutting the image up into smaller pieces. The program is being written in C so i cant really just use a shell script. Thanks for the imagemagick link. I'll take a look at it, and hopefully it'll be what i'm looking for.[/quote]

Check out [http://www.imagemagick.org/script/magick-wand.php](http://www.imagemagick.org/script/magick-wand.php).

---

### Post by spaceballl on 2006-02-23
hmmmm I installed it w/ synaptic.

does anyone know what header file to include in my code? Or does anyone know what library file to link with? Thanks!

-Kevin

---

### Post by hod139 on 2006-02-23
After installing imagemagick, check out the MagicWand API that I posted in my previous post.  [http://www.imagemagick.org/script/magick-wand.php](http://www.imagemagick.org/script/magick-wand.php)  "The MagickWand API is the recommended interface between the C programming language and the ImageMagick image processing libraries."

The site linked above gives documentation and examples.

---

