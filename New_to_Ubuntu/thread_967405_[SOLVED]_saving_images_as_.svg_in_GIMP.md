---
title: "[SOLVED] saving images as .svg in GIMP"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by justchange on 2008-11-02
Can I get GIMP help here?

Just for fun, I decided make my own playing card set by altering a copy of the installed card image.

When I went to save, GIMP doesn't seem to offer .svg as an extension option.
[LIST=1]
[*]Did I miss something?
[*]Can the gnome games recognize other image formats?
[*]Can I add support for other image formats to GIMP? How?
[/LIST]

Did I mention that I'm a total nUUb here in Linux-land? Go easy on the command-line stuff, k?
Thanks

---

### Post by ad_267 on 2008-11-02
Gimp is a raster graphics editor, not a vector editor. If you want to edit svg files get inkscape (available from Add/Remove applications or System - Administration - Synaptic).

Gimp can only import the svgs. See [http://en.wikipedia.org/wiki/Vector_graphics](http://en.wikipedia.org/wiki/Vector_graphics)

---

### Post by ad_267 on 2008-11-02
Perhaps I didn't explain myself well enough because you thought it was necessary to make a duplicate post at [http://ubuntuforums.org/showthread.php?p=6085689](http://ubuntuforums.org/showthread.php?p=6085689).

SVG is a vector graphics format. Vector graphics uses lines and shapes to describe the image as explained in the wikipedia article. The GIMP is a raster graphics editor. Raster graphics describe the image in terms of pixel colours.

GIMP can import an SVG, converting it from a vector to a raster image. The GIMP **cannot** save as SVG because vector graphics are a completely different thing to raster graphics.

You're only options are that the gnome games can use a png card set or that you redo your work in Inkscape or any other vector graphics editor that supports svg.

---

### Post by justchange on 2008-11-02
AD-267, thanks for your helpful suggestions.
I will get that app.

Sorry I didn't respond sooner, I took the last hour off to watch UFC Wired.

The image editors I am accustomed to using (PS and PSP) can handle both formats, so I was expecting the same with GIMP.

As for the duplicate post... it was unintentional (I think I was trying to make an edit and clicked the wrong button), so, thanks to your url posting I found it and I have deleted it.

Thanks for pointing it out.

---

### Post by ad_267 on 2008-11-02
I haven't used photoshop much so I don't know how it handles vector and raster graphics, but Inkscape is more like Adobe Illustrator if you've used that and is much more suited to editing SVGs than GIMP.

If you've done heaps of work on the cards in GIMP already and gnome games won't use another format other than svg it might be possible to import the bitmaps into inkscape and then save them as an svg containing an embeded bitmap image. Inkscape also has a bitmap tracing tool that you could try using to convert your images into a vector.

---

### Post by justchange on 2008-11-02
Wow!
Much more information than I had counted on!
Thanks!

I keep Photoshop around for those *absolutely necessary* projects, but I mostly use older versions of Paint Shop Pro (v.7 -v.9).

In both programs, individual layers can be inserted as either raster or vector, and the various layers interleaved.
Of course, the available tools vary depending on the layer format.
And when saving, layers are converted, depending on saved format.

It looks like I've got a lot of exploring to do.
Thanks for your input.

---

### Post by dariusdwtt on 2008-12-07
bump

---

### Post by egawrangler on 2009-01-12
> **ad_267 said:**
> Perhaps I didn't explain myself well enough because you thought it was necessary to make a duplicate post at [http://ubuntuforums.org/showthread.php?p=6085689](http://ubuntuforums.org/showthread.php?p=6085689).


The user is new, they need help, so they posted multiple threads in an attempt to widen the search-resolution space (even if absent-mindedly).  Are glib cracks like this really necessary from such a senior poster?  Everyone has to start somewhere, spare me the time/thread space wasted argument.

Anyways, ignoring the unnecessary arrogance, you answered the question and it helped me out, so I thank you for that.

-EGA

---

