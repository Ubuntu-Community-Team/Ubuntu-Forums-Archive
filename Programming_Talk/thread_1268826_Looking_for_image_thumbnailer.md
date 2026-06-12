---
title: "Looking for image thumbnailer"
date: 2009-09-17
forum: Programming Talk
---

### Post by bruce2000 on 2009-09-17
Hi

I'm looking for software to create image thumbnails and generate HTML, in order to create a web page gallery of photos (client side for Linux)

Something like SmallerAnimals' Thumbnailer for windows would be ideal... but it doesn't have to be so full-featured, as I know that is asking a lot.

I've tried searching various places and not had much luck - I found only one program called PicturePages, but I didn't like it/was kinda basic.

I'd prefer something for Linux but would consider Windows if necessary as I'm dual booting.

Any suggestions?

---

### Post by jpkotta on 2009-09-17
There's always convert from ImageMagick.  Not the most user friendly but great if you have a rigid format and lots of images.  Here is a convert command I use in a script:

```

    nice -n 19 xwd -silent -id ${w.id} | \
    convert -size 256x192 -thumbnail '252x188>' \
        -bordercolor transparent -border 128 \
        -gravity center -crop 256x192+0+0 \
        xwd:- png:${SCREENSHOT_ICONDIR}/${w.id}_big.png >/dev/null 2>&1 & \
    nice -n 19 convert -filter sinc -resize '128x96!' \
        png:${SCREENSHOT_ICONDIR}/${w.id}_big.png png:${SCREENSHOT_ICONDIR}/${w.id}.png >/dev/null 2>&1 &

```

What this does is take a screenshot of a window and generates both  256x192 and 128x96 thumbnails, with the actual screen capture centered and maximized (but not distorted) in the thumb, and with any excess pixels transparent (also a 2 pixel border).

---

### Post by gordintoronto on 2009-09-18
Photon!  If you have a bunch of images, one command will generate the thumbnails and all the HTML.  Oh, sorry, it's a command-line program.

You can specify how many rows and columns there should be on your thumbnail pages.

I was surprised by how fast it is.

It can also resize your images, optionally into multiple sizes, but I didn't try that because my images are a mix of portrait and landscape, and it's not obvious whether Photon can handle that appropriately.

---

### Post by bruce2000 on 2009-09-18
I was thinking about using imagemagick for the thumbnails and writing my own python script for the html, if i couldnt find some decent software to do the job.

Ive just installed photon and will have a wee play around with it, command line is no problem

Thank you!

---

### Post by stderr on 2009-09-19
Personally, (somewhat depending on the actual usage scenarios), I'd just use CSS and a little javascipt/perl/PHP/whatever you like to set the image's width & height. I usually use some MAX_DIMENSION variable, take the largest measurement (width or height depending), scale it down to MAX_DIMENSION, and then apply the scaling factor to the other dimension too. This way, you don't need to worry about thumbnail generation; it happens dynamically as requested. On the other hand, server CPU utilisation goes up, unless you offload it to the client by using javascipt: not necessarily ideal either.

edit: Oh, and if you need to support IE, then it should be noted that it (at least IE6) can be buggy with regard to getting image width & heights in Javascipt, and I haven't found any workarounds.

---

### Post by phillw on 2009-09-19
I've not started 'playing' with this to any real extent, but I'm hopeful that this 'wee-beastie' will be handle my resizing etc ....

[http://trac.gxdlabs.com/projects/phpthumb/wiki/Docs/BasicUsage](http://trac.gxdlabs.com/projects/phpthumb/wiki/Docs/BasicUsage)

It seems well documented - so, I'm keeping my fingers crossed :)

Regards,

Phill.

---

### Post by hessiess on 2009-09-19
> **stderr said:**
> Personally, (somewhat depending on the actual usage scenarios), I'd just use CSS and a little javascipt/perl/PHP/whatever you like to set the image's width & height. I usually use some MAX_DIMENSION variable, take the largest measurement (width or height depending), scale it down to MAX_DIMENSION, and then apply the scaling factor to the other dimension too. This way, you don't need to worry about thumbnail generation; it happens dynamically as requested. On the other hand, server CPU utilisation goes up, unless you offload it to the client by using javascipt: not necessarily ideal either.

edit: Oh, and if you need to support IE, then it should be noted that it (at least IE6) can be buggy with regard to getting image width & heights in Javascipt, and I haven't found any workarounds.

This won't produce the best looking results, browsers still use nearest neighbour filtering for resizing images which looks ugly, best to convert them server side using bilinear or bi-cubic interpolation.

---

### Post by bruce2000 on 2009-09-21
I wondered if there would be a server side solution, but ive never done any web scripting before so i dont fancy going that route

I tried photon but it comes up with an error half way thru, also it doesnt really have enough features for what i need

Right now im thinking of just buying the thumbnailer from smalleranimals, which is excellent

either that or writing my own

Thanks for the replies.

---

