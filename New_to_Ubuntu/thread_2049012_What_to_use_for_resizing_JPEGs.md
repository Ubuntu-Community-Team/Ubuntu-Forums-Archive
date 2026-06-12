---
title: "What to use for resizing JPEGs?"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Raphicerus on 2012-08-27
Hi All,

I'm a former IrfanView user, and not sure what to use in Ubuntu

Before too long I'm going to have to resize some images and reduce the JPEG quality for Web use. Is it time to install GIMP, or is that complete overkill?

I know I could probably install Wine and run IrfanView, but I'm aiming for 100% pure Linux here. :D

---

### Post by mike555 on 2012-08-27
You might want to install " MTpaint " it is light and does so much .....

---

### Post by alphacrucis2 on 2012-08-27
> **Raphicerus said:**
> Hi All,

I'm a former IrfanView user, and not sure what to use in Ubuntu

Before too long I'm going to have to resize some images and reduce the JPEG quality for Web use. Is it time to install GIMP, or is that complete overkill?

I know I could probably install Wine and run IrfanView, but I'm aiming for 100% pure Linux here. :D

If you want to do batches of files then use imagick from the command line

[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)

There are probably nautilus plugins that will do it via the file right click menu if you want a graphical way of doing it without a full image manipulation program like Gimp or Krita

---

### Post by Raphicerus on 2012-08-27
> **mike555 said:**
> You might want to install " MTpaint " it is light and does so much .....

I'll look into that, thanks. It sounds like a good one.

> If you want to do batches of files then use imagick from the command line

[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)
 

Ah, now that is interesting. I was thinking of cooking my entire photo collection to fit on an Archos 405 with 32GB card.

---

### Post by Buntu Bunny on 2012-08-27
Actually, you might like Gimp. I use it most for cropping, re-sizing, and optimizing photos for uploading onto the internet. It takes a little getting used to, but I think it's worth it. 

Other than that, you can always use a free online resizer:
[http://www.picresize.com/](http://www.picresize.com/)
[http://www.shrinkpictures.com/](http://www.shrinkpictures.com/)
[http://www.webresizer.com/](http://www.webresizer.com/)
[http://www.resizr.com/](http://www.resizr.com/)
etc.

---

### Post by ajgreeny on 2012-08-27
The best way is undoubtedly the nautilus plugin way.

The name of the plugin package has changed since 10.04 which is the ubuntu version I still use and where the name is **nautilus-image-converter**, but search for nautilus in the software center (or better in synaptic) and you'll quickly find what you want.  Then it's a right click and you can resize or rotate as you want, with lots of naming, size, and rotation angle options.

---

### Post by Raphicerus on 2012-08-27
> **Buntu Bunny said:**
> Actually, you might like Gimp. I use it most for cropping, re-sizing, and optimizing photos for uploading onto the internet. It takes a little getting used to, but I think it's worth it. 

Other than that, you can always use a free online resizer:
[http://www.picresize.com/](http://www.picresize.com/)
[http://www.shrinkpictures.com/](http://www.shrinkpictures.com/)
[http://www.webresizer.com/](http://www.webresizer.com/)
[http://www.resizr.com/](http://www.resizr.com/)
etc.

Ah, more information. I will be installing and learning GIMP, but I suspected I was about to call in an artillery strike on a mouse infestation. ;) I hope it's a bit less arcane than PhotoShop.

> The best way is undoubtedly the nautilus plugin way.

The name of the plugin package has changed since 10.04 which is the ubuntu version I still use and where the name is **nautilus-image-converter**,  but search for nautilus in the software center (or better in synaptic)  and you'll quickly find what you want.  Then it's a right click and you  can resize or rotate as you want, with lots of naming, size, and  rotation angle options. 

Sounds good for single images, which come up a lot in email. Thanks.

---

### Post by Buntu Bunny on 2012-08-27
> **Raphicerus said:**
> Ah, more information. I will be installing and learning GIMP, but I suspected I was about to call in an artillery strike on a mouse infestation. ;) I hope it's a bit less arcane than PhotoShop.

Suggest Gimp 2.8. Version 2.6 is in the Ubuntu Softward center, but I like 2.8 much better. Instructions to install from PPA, here - [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html)

---

### Post by ajgreeny on 2012-08-27
> **Raphicerus said:**
> Ah, more information. I will be installing and learning GIMP, but I suspected I was about to call in an artillery strike on a mouse infestation. ;) I hope it's a bit less arcane than PhotoShop.



Sounds good for single images, which come up a lot in email. Thanks.

The plugin can work on batches as well, as long as the sizing or rotation is the same for all of them, but that's the situation for any batch editing.  You just select all the images you want to edit and right click in them.

---

### Post by stmiller on 2012-08-27
imagemagick.

```
sudo apt-get install imagemagick
```

Destructively resize:

```
mogrify -resize 1024x768 *.jpg
```


The command convert will also do this, non-destructively.

---

### Post by Raphicerus on 2012-08-28
Thanks for the suggestions, everyone. The Nautilus plugin did a  reasonable job. It also installed the ImageMagick tools behind the  scenes. I found a heavily downsized JPEG could be produced with

```

convert input.jpg -resize 640x480 -quality 10 output.jpg

```Thanks again. Another one solved!

---

### Post by RedRat on 2012-08-28
Gimp is ok if you want to be a pro along the lines of Adobe Photoshop, but I would suggest DigiKam. This gives you a light table so you can organize your files and do batch operations, e.g., resizing or converting from one format (e.g., bmp to jpg or vice-versa) to another. The learning curve is rather short and easy. There are quite a bunch of plugins that come with it so that you can color control your pix.

---

### Post by Raphicerus on 2012-08-28
> **RedRat said:**
> Gimp is ok if you want to be a pro along the lines of Adobe Photoshop, but I would suggest DigiKam. This gives you a light table so you can organize your files and do batch operations, e.g., resizing or converting from one format (e.g., bmp to jpg or vice-versa) to another. The learning curve is rather short and easy. There are quite a bunch of plugins that come with it so that you can color control your pix.

Thanks for the "heads up", RedRat. I never was the pro image manipulator, just the '86 assembler and C type. I felt very sorry for the talented art staff at work, who had to contend with all those unintuitive interfaces.

I'll have a look at DigiKam. It only needs to do what IrfanView did, to keep me happy.:D

---

### Post by RedRat on 2012-08-28
> **Raphicerus said:**
> Thanks for the "heads up", RedRat. I never was the pro image manipulator, just the '86 assembler and C type. I felt very sorry for the talented art staff at work, who had to contend with all those unintuitive interfaces.

I'll have a look at DigiKam. It only needs to do what IrfanView did, to keep me happy.:D
[Raphicerus]("http://ubuntuforums.org/member.php?u=1719365")
When I was in the Windows world, I used a very simple program called ThumbsPlus (with some futzing about, you can install it under Ubuntu using Wine) and DigiKam sort of reminds me of ThumbsPlus. Even in resizing, you may also want to reduce the "dpi" of the image, this also makes the pictures smaller. DPI can be much smaller for web pages along with smaller in terms of pixels width and length. DigiKam can do this.

---

### Post by ajgreeny on 2012-08-29
> **RedRat said:**
> [Raphicerus]("http://ubuntuforums.org/member.php?u=1719365")
When I was in the Windows world, I used a very simple program called ThumbsPlus (with some futzing about, you can install it under Ubuntu using Wine) and DigiKam sort of reminds me of ThumbsPlus. Even in resizing, you may also want to reduce the "dpi" of the image, this also makes the pictures smaller. DPI can be much smaller for web pages along with smaller in terms of pixels width and length. DigiKam can do this.
If the OP does that he might as well install irfanview which works very well with wine.  It is even suggested on the irfanview website as a reason for the application writer not to bother with a native Linux version.

---

### Post by RedRat on 2012-08-29
> **ajgreeny said:**
> If the OP does that he might as well install irfanview which works very well with wine.  It is even suggested on the irfanview website as a reason for the application writer not to bother with a native Linux version.
Having installed my ThumbsPlus on several Linux machines under wine, I hope that installation goes a bit easier. Some Windows programs do not go easily, especially later Ubuntu and Mint versions. It was easier for me to get an older version of ThumbsPlus installed on 8.04 than in 10.04 and 12.04. I have yet to get it installed in Mint 13!

My point here is that DigiKam is there in the repositories and ready to go. It is pretty straight forward, a bit of a learning curve but not that bad.

---

### Post by Raphicerus on 2012-08-29
> 
My point here is that DigiKam is there in the repositories and ready to  go. It is pretty straight forward, a bit of a learning curve but not  that bad.


Ah, that's what I thought you meant, Red Rat. I haven't tried it yet.

My late unlamented Vista installation had a ton of batch files on it, so I've been having fun learning the art of shell scripting. 

I was about to ask a question about editors, but I'll start a new thread.

---

### Post by JKyleOKC on 2012-08-29
You might like "fotoxx" from [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) which is about as simple as IrfanView; I've found that it can do some things that I could not accomplish with Gimp (specifically removing the tilted-back distortion on shots of tall buildings).

However for mass-production use, resizing dozens of images at once to fixed size, ImageMagick has no equal because you can create simple scripts for it. [http://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/](http://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/) tells how, and a more extensive document is at [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

Hope this helps!

---

### Post by Easy Limits on 2012-08-30
showFoto

---

### Post by Raphicerus on 2012-08-30
> **JKyleOKC said:**
> You might like "fotoxx" from [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) which is about as simple as IrfanView; I've found that it can do some things that I could not accomplish with Gimp (specifically removing the tilted-back distortion on shots of tall buildings).

However for mass-production use, resizing dozens of images at once to fixed size, ImageMagick has no equal because you can create simple scripts for it. [http://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/](http://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/) tells how, and a more extensive document is at [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

Hope this helps!

It's interesting to know that shift and tilt corrections are available.

While I was working out how to do do basic jpeg downscaling, I was reading about ImageMagick parameters, and was amazed by the sheer scale of the thing. Forth Bridge or what? :D

How many man years of development in it, I wonder?

---

### Post by Raphicerus on 2012-08-30
Ah, useful links, especially for a scripting fiend.
Saved for tomorrow.

---

