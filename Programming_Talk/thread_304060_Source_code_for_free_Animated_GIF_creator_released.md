---
title: "Source code for free Animated GIF creator released"
date: 2006-11-21
forum: Programming Talk
---

### Post by Velotix on 2006-11-21
(I had no idea where to put this, so I apologise if it's in the wrong place.)

On [this web page](http://www.whitsoftdev.com/unfreez/) you can download a program for Windows called UnFREEz which allows you to create animated images in GIF format. I once used it extensively and found it very efficient at doing its job, though it's very basic.

I always thought this program was only freeware, but it turns out that he's offered the source code for download, so I guess it's not.

Anyway, I figure that now the patenting issues are no longer relevant, this can be ported to Linux without much hassle at all. So I'm letting people know of its existence here.

Why do I not do this myself? I suck at programming right now. :P I'm sure one of you folks could whip something up a lot quicker than me.

Just putting this out there. Apologies if I've overlooked something important. ^^

---

### Post by red_Marvin on 2006-11-21
Gimp can save layers as frames if gif is chosen as the save format...;)

---

### Post by ironfistchamp on 2006-11-21
Personally I found GIMP quite poor when it came to making Gifs. It never seemed to work right. Can't really explain it but I would like to see a program that was explicitly developed for Gif animation purposes. Too bad I am not good enough to port it.

Ironfistchamp

---

### Post by hod139 on 2006-11-21
imagemagick can make animated gifs, among handling almost every other image format.

---

### Post by kperkins on 2006-11-23
Looks like the only thing that this prog will do, that gimp doesn't, is set how many times to loop the gif.  I don't really see any benefits to it, since if you want to set the number of times to loop there you can do it with gifsicle (actually making a gui for gifsicle would probaly be easier than porting this, since there are lots of calls to the Windows api in the code I  looked at, and you'd have to redo the whole gui anyways since it uses MS Developer Studio for the gui building.) Also, it is not GPL'd.  
" "LegalCopyright", "Copyright © 2001 WhitSoft Development" "

---

### Post by billynomates on 2008-07-24
This post was ages ago, but in case anyone is looking.

When you save a gif in GIMP, it asks gives you the option to roll the layers through as an animation, and the delay between each one.

---

