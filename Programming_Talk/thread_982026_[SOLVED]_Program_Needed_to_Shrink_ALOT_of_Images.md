---
title: "[SOLVED] Program Needed to Shrink ALOT of Images"
date: 2008-11-14
forum: Programming Talk
---

### Post by dhtseany on 2008-11-14
Hey all,
I want to write a program that I will use to take images that are ~1MB in size and shrink them to ~300kb. The following are the requirements for the app:

1) To start it must be Window$ based (I know, I know...;))
2) Must be stand alone (i.e. I would like to avoid a ton of extra packages to be installed with it. .NET and VB should be ok though)
3) Must be able to handle a ton of images (500+) at once
4) Must be able to handle JPG. PNG, GIF and BMP would be a plus but not required.

I have heavy experience using PHP, HTML, and MySQL. I have below average skills using Java and Basic. 

So where can I start? Of course I don't expect anyone to write it for me :) I just need help getting pointed in the right directions.

Peace
Sean

---

### Post by rjack on 2008-11-14
All you need is ImageMagik's convert.

Windows binary: [http://www.imagemagick.org/script/binary-releases.php#windows](http://www.imagemagick.org/script/binary-releases.php#windows)

You can run it in a batch script, but I'd prefer to install cygwin and use the ol' good bash.

---

### Post by Kilon on 2008-11-14
Start from here.Google Magic.

[http://forums.sun.com/thread.jspa?threadID=522483](http://forums.sun.com/thread.jspa?threadID=522483)
[http://www.java2s.com/Code/CSharp/2D-Graphics/ShrinkImage.htm](http://www.java2s.com/Code/CSharp/2D-Graphics/ShrinkImage.htm)
[http://www.componenthouse.com/article-20](http://www.componenthouse.com/article-20)
[http://www.kitfox.com/javaOne2007/javaOne-notes.pdf](http://www.kitfox.com/javaOne2007/javaOne-notes.pdf)
[http://www.informit.com/content/images/0201700743/samplechapter/rodriguesch7.pdf](http://www.informit.com/content/images/0201700743/samplechapter/rodriguesch7.pdf)
[http://www.corewebprogramming.com/PDF/ch10.pdf](http://www.corewebprogramming.com/PDF/ch10.pdf)
[http://www.java-tips.org/java-se-tips/java.awt.image/shrinking-an-image-by-skipping-pixels.html](http://www.java-tips.org/java-se-tips/java.awt.image/shrinking-an-image-by-skipping-pixels.html)
[http://www.digitalsanctuary.com/tech-blog/java/how-to-resize-uploaded-images-using-java.html](http://www.digitalsanctuary.com/tech-blog/java/how-to-resize-uploaded-images-using-java.html)
[http://www.koders.com/java/fid575707A0F7E6FE0E56C7CEAB21CDAFFDC9774C8D.aspx](http://www.koders.com/java/fid575707A0F7E6FE0E56C7CEAB21CDAFFDC9774C8D.aspx)

---

### Post by gpsmikey on 2008-11-14
See if the FREE irfanview meets your needs.
[http://www.irfanview.com](http://www.irfanview.com) - freeware and the guy that wrote it is very good with his support and upgrades to it.  It has a batch mode where you can do all sorts of things to the selected images (including "tweaking" them as you shrink them and specifying the output directory).  Almost everyone I know on the windows side who works with images has it (they may also have photoshop etc, but this is sort of the "swiss army pocket knife").

mikey

---

### Post by Kevbert on 2008-11-14
I use PixResizer for batch re-sizing in Windows which can be found [[COLOR="Red"]here[/COLOR]]("http://bluefive.pair.com/pixresizer.htm").

---

### Post by juicymixx on 2008-11-14
> **gpsmikey said:**
> See if the FREE irfanview meets your needs.
[http://www.irfanview.com](http://www.irfanview.com) ... 


Irfanview definitely fits the bill.   It can batch downsize all the images in a directory pretty quickly...

If you really want to write a program, then you'll have to learn about the different types of images you want to work with, and methods of reducing their filesize in an acceptable way (meaning, how bad do you want to downgrade the actual image).

---

### Post by drubin on 2008-11-15
> **dhtseany said:**
> Hey all,
**1) To start it must be Window$ based (I know, I know...;))**
[http://www.vso-software.fr/products/image_resizer/](http://www.vso-software.fr/products/image_resizer/)

---

### Post by dhtseany on 2008-11-16
Hey guys thanks alot! I'm gonna play around with this today and see which works best.

I'll post back my pick :)

Peace
Sean

---

### Post by iponeverything on 2008-11-16
If you see the light and want to do under linux:

```
ls *jpg |awk '{print "convert "$1" -resize 30% small-"$1}'|sh &
```

This command will resize all the images in a directory and give you a small version with a prefix of "small-"  so for instance you will have dscn2345.jpg (the orginal) and small-dscn2345.jpg (the shrunk one)

Change the % for more or less shrinkage.

---

### Post by dhtseany on 2008-11-18
> **iponeverything said:**
> If you see the light and want to do under linux:

```
ls *jpg |awk '{print "convert "$1" -resize 30% small-"$1}'|sh &
```

This command will resize all the images in a directory and give you a small version with a prefix of "small-"  so for instance you will have dscn2345.jpg (the orginal) and small-dscn2345.jpg (the shrunk one)

Change the % for more or less shrinkage.

Haha thanks for the tip; I'll give it a shot. It had to be Windows based due to my customer is running XP. I set him up with the IRview and he loves it.

Thanks
Sean

---

