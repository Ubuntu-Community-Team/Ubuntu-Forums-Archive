---
title: "Need an application to compress images without quality lost in Ubuntu"
date: 2023-04-02
forum: New to Ubuntu
---

### Post by desatir73162 on 2023-04-02
Hi there
I am looking for an application to reduce image size without quality lost. 
Not important it will work only in terminal or has GUI, just want the best result from it.
If it can change the height and width of the picture, its a better fit for me.

I googled it and found a bunch of options but I do not know which on is the hero in the field.

Current OS: Ubuntu 22.04

Thanks in advanced.

---

### Post by Autodave on 2023-04-02
Realize that if you compress a graphics file with any program, there will always be a loss in quality.  How much is lost depends somewhat on the program that you select, but it depends more on how much that you compress it.

---

### Post by desatir73162 on 2023-04-02
I am just looking for a program for the most compress and the least quality lost.
In the past i used "caesium" or tinypng.com. Unfortunately the caesium is only available for mac and windows. The tinypng.com in the other hand, has a slow workflow (upload, download, ... )
I just want a handy tool.

Thanks

---

### Post by Holger_Gehrke on 2023-04-02
A command line version of caesium is available for Linux, but only as source at [https://github.com/Lymphatus/caesium-clt](https://github.com/Lymphatus/caesium-clt) . For PNG images there's 'optipng', it's in the repositories. Beyond that, I'd check [https://alternativeto.net](https://alternativeto.net) .

Holger

---

### Post by #&amp;thj^% on 2023-04-02
Just to add another thought: [https://github.com/Huluti/Curtail](https://github.com/Huluti/Curtail)
has both flatpak and PPA method on the link.
Compress your images
Curtail (previously ImCompressor) is an useful image compressor, supporting PNG and JPEG file types. It support both lossless and lossy compression modes with an option to whether keep or not metadata of images. It is inspired by Trimage and Image-Optimizer.

---

### Post by mIk3_08 on 2023-04-02
> **desatir73162 said:**
> In the past i used "caesium" 
I agree with Holger. caesium command line version works smoothly in my Ubuntu System. I have tried this one and its perfect. No issue so and best compression so far with minimal losses. Regards and cheers.
> **Holger_Gehrke said:**
> A command line version of caesium is available for Linux, but only as source at [https://github.com/Lymphatus/caesium-clt](https://github.com/Lymphatus/caesium-clt) . For PNG images there's 'optipng', it's in the repositories. Beyond that, I'd check [https://alternativeto.net](https://alternativeto.net) .
Holger

---

### Post by desatir73162 on 2023-04-03
> **Holger_Gehrke said:**
> A command line version of caesium is available for Linux, but only as source at [https://github.com/Lymphatus/caesium-clt](https://github.com/Lymphatus/caesium-clt) . For PNG images there's 'optipng', it's in the repositories. Beyond that, I'd check [https://alternativeto.net](https://alternativeto.net) .

Holger

As far as I used caesium before and liked it, I think its a better choice for me! And that alternative website is great too. 
Thanks

---

### Post by ActionParsnip on 2023-04-03
Could look into imagemagick

---

### Post by desatir73162 on 2023-04-03
I tried to install caesium by follwing command:
> 
cargo build --release


It done without any error but now it seems terminal does not know this program:
> 
caesiumclt: command not found


what should i do now?

---

### Post by desatir73162 on 2023-04-03
Finally Done!
The last step is to add "caesium-clt-main/target/release/" to the $PATH and logout/login.

Now it works. 
Thanks a lot people who helped me.

---

### Post by TheFu on 2023-04-03
I use ImageMagick's 'convert' tool for this.  Usually there is a specific target for viewing.  So if you have a 50MB image file, but it will only bee seen on a 1920x1080 screen, then you can easily compress that (losing lots and lots of information, that nobody can see).


```
#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   /usr/bin/convert  -quality $QUAL  "$img"  "$NEW"
done
```
Screw with the "QUAL" setting. Also, since it is one of my scripts, filenames with spaces aren't allowed.  I've had some images conversions at 20% quality turn out very nice.

If you want to resize the image, that can also be accomplished. The manpage for convert is pretty clear. If you provide half the new size, then the aspect ratio will be maintained automatically. That script:
```
#!/bin/bash

NEW_SIZE="640x"
QUAL="40"

for img in "$@"; do
  echo " Working on $img ..."
  convert -resize $NEW_SIZE "$img" "$img-new"
  convert -quality $QUAL  "$img-new"  "$img"

done

```

---

### Post by Holger_Gehrke on 2023-04-04
@TheFu: Why are you doing two convert runs ? You can give both options to convert ('convert -quality $QUAL -resize $NEW_SIZE ...'). Generational loss is a thing with lossy compression, so one should do as few conversions as possible to keep the loss under control. Also you're overwriting the original file in the second script and keeping the intermediate image which was only resized, I'm not sure that's intentional or wanted.

While the manual page for convert is okay, some of the options and parameters to the options do need a lot more explaining than the manual page provides. There is a package named imagemagick-doc or imagemagick-6-doc which installs html documentation into /usr/share/doc/imagemagick-6-doc/html/www/ (kind of hard to read that if you're using a browser installed as snap ...). That documentation goes into a lot more detail than the manpages provide. There's also [https://www.imagemagick.org/script/convert.php](https://www.imagemagick.org/script/convert.php) which gives the same information online.

Holger

---

### Post by TheFu on 2023-04-04
> **Holger_Gehrke said:**
> @TheFu: Why are you doing two convert runs ? You can give both options to convert ('convert -quality $QUAL -resize $NEW_SIZE ...'). Generational loss is a thing with lossy compression, so one should do as few conversions as possible to keep the loss under control. Also you're overwriting the original file in the second script and keeping the intermediate image which was only resized, I'm not sure that's intentional or wanted.

Agreed. At the time the script was created, I didn't know that all transformations could be put into a single run.  These are over 20 yrs old and the results have been fine, so I never bothered to fix them.1

As for overwriting the files or not.  I wasn't as good with backups when the first was created as compared to a few years later when the 2nd script was needed. It was being used for a web-site gallery, so I needed a specific resolution.

All of us get better over many years, but we don't start out knowing as much as we'd like. ;)

> **Holger_Gehrke said:**
> While the manual page for convert is okay, some of the options and parameters to the options do need a lot more explaining than the manual page provides. There is a package named imagemagick-doc or imagemagick-6-doc which installs html documentation into /usr/share/doc/imagemagick-6-doc/html/www/ (kind of hard to read that if you're using a browser installed as snap ...). That documentation goes into a lot more detail than the manpages provide. There's also [https://www.imagemagick.org/script/convert.php](https://www.imagemagick.org/script/convert.php) which gives the same information online.

That's useful.  I use lynx or dillo locally to read html files.

---

### Post by Impavidus on 2023-04-04
This is really more a question of what file format to use than about what application to use. JPEG offers good compression, is lossy, but generally looks OK for photos if you don't compress too aggressively. For schematics, it's not so good. PNG is lossless, offers much less compression for photos, but better quality for schematic images. I expect that a large part of the applications that offer JPEG use libjpeg under the hood and a large part of the applications that offer PNG use libpng under the hood. With the same software under the hood, the same compression level will give you the same quality and filesize.

---

### Post by TheFu on 2023-04-04
> **Impavidus said:**
> This is really more a question of what file format to use than about what application to use. JPEG offers good compression, is lossy, but generally looks OK for photos if you don't compress too aggressively. For schematics, it's not so good. PNG is lossless, offers much less compression for photos, but better quality for schematic images. I expect that a large part of the applications that offer JPEG use libjpeg under the hood and a large part of the applications that offer PNG use libpng under the hood. With the same software under the hood, the same compression level will give you the same quality and filesize.

It comes down to compromise.  For example, I have a number of MS-Visio diagrams. These are all vector drawings, so infinitely scalable without loss, but when it is time to share them, like on a website, we can't post Visio files.  We need "good enough" images for the target viewers.  Here's an image: [https://blog.jdpfu.com/images/KVM-howto-opt.jpg](https://blog.jdpfu.com/images/KVM-howto-opt.jpg)  A full page image which could have been 5+ MB, but running it through convert created a 61KB file that is clear enough to be used, even with all the information it contained.  BTW, that image is out-of-date, since the "interfaces" file is deprecated.  Zooming in using a browser zoom, <cntl>-+, capability will show the image flaws.  The thumbnail is under 4Kb.

I think PNG can do lossy compression. [https://www.howtogeek.com/203979/is-the-png-format-lossless-since-it-has-a-compression-parameter/](https://www.howtogeek.com/203979/is-the-png-format-lossless-since-it-has-a-compression-parameter/)

---

### Post by Holger_Gehrke on 2023-04-04
For vector graphics on the web SVG (Scalable Vector Graphics) is the format of choice and has been for the last decade. All the major browsers support it, even MS Edge and Opera did before they became just more chromium reskins. Beware, though: the drawing needs to have a viewbox defined. Older versions of Inkscape didn't do this, the one you get from the repositories on 22.04 does.

And no, PNG can't do lossy compression. It can do several levels of compression, basically taking more or less time to search for all the things that can be compressed (similar to the number options of zip (-0,-1,-2 ... -9)).

Holger

---

### Post by TheFu on 2023-04-04
> **Holger_Gehrke said:**
> For vector graphics on the web SVG (Scalable Vector Graphics) is the format of choice and has been for the last decade. All the major browsers support it

Very true, but if the drawing program doesn't output SVG, there's nothing to be done.
Put this into a file.svg:
```
<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="800">
<rect width="1200" height="800" fill="#005BBB"/>
<rect width="1200" height="400" y="400" fill="#FFD500"/>
</svg>
```
Much more efficient than any image. Heck, I bet the headers for jpg/png are larger than that entire file.

I know that newer versions of MS-Visio can output SVG, but not the version I learned and have a license to use.  Seldom is "new" better, but that would certainly be the case.

---

### Post by mIk3_08 on 2023-04-05
> **desatir73162 said:**
> Finally Done!
The last step is to add "caesium-clt-main/target/release/" to the $PATH and logout/login.

Now it works. 
Thanks a lot people who helped me.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by desatir73162 on 2023-04-06
> **mIk3_08 said:**
> On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.
Where is "Solve thread" link? I cant find it.

---

### Post by TheFu on 2023-04-06
"Thread Tools" button.

---

