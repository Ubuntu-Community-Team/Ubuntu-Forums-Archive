---
title: "choppy video play with VLC"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by jediken21 on 2008-09-26
I'm using ubuntu 8.04 and have a strange issue. When I play a video, in this case they are .avi files, with VLC it is very choppy. What's weird is, in my Compiz setting manager, when I enable or disable any option the video plays fine for about 5-10 seconds then goes back to being very choppy. I don't know if this is an issue with vlc & compiz or just a coincidence. Also does this with Totem movie player.

---

### Post by Sirron on 2008-09-26
To narrow it down a bit...

Press Alt+F2, and type:

metacity --replace

this will temporarily disable compiz/beryl; then try playing the video again.

To get compiz back, log out then back in or press Alt-F2 again and type

compiz --replace

---

### Post by jediken21 on 2008-09-26
Yup, plays perfectly now. Is there any way to get around playing it with compiz still on, or will I have to switch each time I want to watch a video?

---

### Post by Sycron on 2008-09-26
Update to the latest video drivers. You have ATI or nVidia, no ?

---

### Post by billgoldberg on 2008-09-26
> **jediken21 said:**
> Yup, plays perfectly now. Is there any way to get around playing it with compiz still on, or will I have to switch each time I want to watch a video?

In the vlc options, tag the advance box in the bottom right.

Then somewhere under video options, set the output to "X11".

This might help, or not, it's worth a shot.

---

### Post by jediken21 on 2008-09-26
> **billgoldberg said:**
> In the vlc options, tag the advance box in the bottom right.

Then somewhere under video options, set the output to "X11".

This might help, or not, it's worth a shot.

thank you sir, that did that trick :D

---

### Post by Sycron on 2008-09-27
Well you can watch movies now :) .:popcorn:

---

### Post by mc4100 on 2008-09-27
> **jediken21 said:**
> thank you sir, that did that trick :D

If you want to achieve the same thing with gstreamer (ie., for videos in Totem), press Alt+F2, and type:
```
gstreamer-properties
```
And set, in the **Video** tab, the **Default Output** to **X11**.

---

