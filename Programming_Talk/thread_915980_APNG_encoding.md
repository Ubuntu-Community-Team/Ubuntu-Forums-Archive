---
title: "APNG encoding"
date: 2008-09-10
forum: Programming Talk
---

### Post by durand on 2008-09-10
I can't find a proper encoder for apngs anywhere on the internet. I think there is one built into firefox but that's not much use to me as I need something that I can encorporate into my program so a python module or a program that I can access via the commandline is ok. Does anyone know where I can find something like this?

Thanks.

---

### Post by hod139 on 2008-09-10
[ImageMagick]("http://www.imagemagick.org/script/index.php") and [libpng]("http://www.libpng.org/pub/png/libpng.html") both support apng.

---

### Post by durand on 2008-09-10
Erm how do I use it with imagemagick? I can't find any documentation and using the same command as for gifs doesn't work...

```
convert -delay 20 -loop 0 *.png anim.png
```

just converts each png separately rather than actually putting it together into an apng.

And I have absolutely no idea how to use libpng. I don't know any C or whatever, just python and bash.

---

### Post by hod139 on 2008-09-10
It looks like I misspoke, imagemagick does [not]("http://www.imagemagick.org/pipermail/magick-developers/2008-April/002942.html") appear to support apngs yet.  Some searching found this firefox add-on: [https://addons.mozilla.org/en-US/firefox/addon/5519](https://addons.mozilla.org/en-US/firefox/addon/5519)

Is that sufficient for what you need?

---

### Post by durand on 2008-09-10
Yeah, I used to use that editor but at the moment it's firefox only. However, the main problem is that I can't use it as part of another program. I need to encode the images and stuff automatically.

---

### Post by hod139 on 2008-09-10
Sorry then, beyond libpng, I do not know of anything else.  There is a tutorial for using libpng to make apngs though if you get desperate and want to try: [http://littlesvr.ca/apng/tutorial/book1.html](http://littlesvr.ca/apng/tutorial/book1.html)

---

### Post by durand on 2008-09-10
Thanks for trying to help. I can't really use libpng. I guess I'll just have to use gifs until it's added to image magick or something more accessible.

---

