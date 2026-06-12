---
title: "Imagemagick/graphicsmagick resizing question"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-09-14
Hi Folks,

I have an image that is 2700x2700.
I want it to be 1280x800

When I try the Imagemagick command 
```
convert <image name> -resize 1280x800 <image name>
```
the image is resized to 800x800

Likewise in Graphicsmagick when I run the command
```
gm mogrify -resize 1280x800 <image name>
```
the image is once again resized to 800x800

If I use GIMP I can resize the image correctly to 1280x800.

Does someone see what bone-head error I am making?

---

### Post by mcduck on 2013-09-14
Sure, the original image is a square 2700x2700, while the resolution you are resizing to would be a different aspect ratio (16:10 instead of the 1:1 of the original). Unless you specifically tell it to, Imagemagick will maintain the original aspect ration and resizes the image to fit inside the resolution you specified.

Try this instead:
```
convert <image name> -resize 1280x800\! <image name>
```

I haven't used Graphicsmagick but I'd assume it follows the same convention as Imagemagick does.

---

### Post by GrouchyGaijin on 2013-09-14
> **mcduck said:**
> Sure, the original image is a square 2700x2700, while the resolution you are resizing to would be a different aspect ratio (16:10 instead of the 1:1 of the original). Unless you specifically tell it to, Imagemagick will maintain the original aspect ration and resizes the image to fit inside the resolution you specified.

Try this instead:
```
convert <image name> -resize 1280x800\! <image name>
```



The magic worked.  I didn't know about the \! (obviously ;))
I thought that supplying the desired dimensions was enough.

Thank you - I've copied your code to my list of notes for future reference.  

Man I like this forum.  Post a question, 20 minutes later a fellow enthusiast gives you the answer.

---

