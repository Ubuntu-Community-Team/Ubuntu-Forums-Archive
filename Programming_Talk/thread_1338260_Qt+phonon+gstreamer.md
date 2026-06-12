---
title: "Qt+phonon+gstreamer"
date: 2009-11-26
forum: Programming Talk
---

### Post by towka on 2009-11-26
Hello programmers!
I have a problem with the phonon + gstreamer in QT4
This piece of code at run-time program throws an exception --

```
(<unknown>:17847): GStreamer-CRITICAL **: gst_element_make_from_uri: assertion `gst_uri_is_valid (uri)' failed
```


&#1057;++ &#1057;ODE:```
Phonon::VideoPlayer* player = new Phonon::VideoPlayer(Phonon::VideoCategory,&l);
player->play(Phonon::MediaSource("/home/user/video1.mpg"));
l.resize(500,500);
l.show();
```

I tried
```
player->play(QUrl::fromLocalFile("/home/user/video1.mpg"));
```
or
```
player->play(QUrl::fromLocalFile("file:///home/user/video1.mpg"));
```
no reactions
What does this mean?

---

### Post by feuera on 2009-12-21
Same problem here ...

Did you try different Qt version?

---

### Post by feuera on 2009-12-21
Actually - your third try using player->play(QUri::fromLocalFile("file:///home...") worked for me ..

regards

---

