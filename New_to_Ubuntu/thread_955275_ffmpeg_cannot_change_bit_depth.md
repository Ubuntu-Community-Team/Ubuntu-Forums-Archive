---
title: "ffmpeg cannot change bit depth"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by susiriss on 2008-10-22
Hi all,
            I have installed ffmpeg from source in my Hardy. I want clips to be converted with a color depth of 12bpp ( bits per pixel). 

I tried with the option -pix_fmt like this, 

```
ffmpeg -i myclip.wmv -vcodec mpeg4 -acodec libfaac -pix_fmt yuyv422 -f avi test.avi
```

But the encoded clip always has color depth 24bpp.

Isn't this the way I should use to convert the color depth. What I am doing wrong.

Thanks
-susiriss

---

### Post by billgoldberg on 2008-10-22
You might get better/more responses here:

[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

---

### Post by susiriss on 2008-10-22
Thanks. I cannot move this thread there so I created a new one in that forum.

---

