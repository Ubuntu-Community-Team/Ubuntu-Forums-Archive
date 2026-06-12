---
title: "What is the fastest way for getting a thumbnail from a jpeg?"
date: 2011-04-28
forum: Programming Talk
---

### Post by TheHimself on 2011-04-28
The only way I know is to use GTK/GDK pixbufs to load the file into a small sized pixbuf and then save it. But this seems to be inefficient. It reads the whole jpeg file to obtain a small thumbnail of it. Does one really have to do so?

By the way, I can't find any documentation for libjpeg online.

---

### Post by bashologist on 2011-04-28
You could use system commands with imagemagick to resize the image and save it in a file. You could use hashes for the filename of the thumbnails. I think that's the only possible way. 

I couldn't say if generating the hash of the file would be more efficient but most filesystem browsers i've seen to this sort of thing so it's probably the way to go. 

You even might be able to find a directory in your filesystem already storing hashed thumbnails for images and videos for example. Nautilus used to do this I think. Good luck.

---

### Post by SeijiSensei on 2011-04-28
[http://www.imagemagick.org/Usage/thumbnails/#creation](http://www.imagemagick.org/Usage/thumbnails/#creation)

You need to install ImageMagick first from the repositories/software center.

---

### Post by TheHimself on 2011-04-28
Thanks. This helps a lot.

---

