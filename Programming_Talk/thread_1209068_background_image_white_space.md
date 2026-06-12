---
title: "background image white space"
date: 2009-07-09
forum: Programming Talk
---

### Post by sandyd on 2009-07-09
Im currently modding an already designed theme.
I wanted to add an extra background picutre... so i did.

I expected the background image to tile (because of different resolution screens), but it tiled with an annoying tiny little white line in between.
Now, i could simply do a 1 pixel width background image, but that would make the whole thing only one color horizontally.

any ideas? 

using phpbb3 with aeroblack theme. 

modified theme upload here
[http://hotfile.com/dl/8261505/b43ed78/AeroBlack.tar.gz.html](http://hotfile.com/dl/8261505/b43ed78/AeroBlack.tar.gz.html)
because it exceded the uplaod file size

---

### Post by myrtle1908 on 2009-07-09
Rather not to wade through 2.5MB of attachment.  Couldn't you simply paste the relevant 'background-image ...' line from your CSS?

I'm guessing you are not setting 'background-position' or something like that so it is defaulting to 'center'.

Try

```
background-image: url(images/yourImage.gif); **background-position: left top;** background-repeat: repeat
```

---

