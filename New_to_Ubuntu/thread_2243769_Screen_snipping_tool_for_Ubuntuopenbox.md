---
title: "Screen snipping tool for Ubuntu/openbox"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by PeterTaps on 2014-09-11
Environment: Ubuntu 14.04 minimal + openbox

I am used to using the snipping tool that comes on Windows. You simply select a window or a region and a copy of the image is saved. I am wondering if there is something similar that works under openbox. Preferably lightweight as I just need to copy a region of the screen and save it as .png or .jpg.

Thank you in advance for your help.

Regards,
Peter

---

### Post by TheFu on 2014-09-11
**import** is the name of the program. It is part of **imagemagick**.  It doesn't have a GUI, so extremely lightweight, as requested.  

import file.jpg  # then use the mouse to select a rectangle to be saved.

---

### Post by vasa1 on 2014-09-11
Looks like OP wants just to select a part of a screen and save the selected part directly rather than edit an image. So maybe something like **scrot -s**?

---

### Post by TheFu on 2014-09-11
> **vasa1 said:**
> Looks like OP wants just to select a part of a screen and save the selected part directly rather than edit an image. So maybe something like **scrot -s**?

**Scrot -s** behaves just like **import** - but seems to be already installed.  Better answer. nice.


However, imagemagick brings other tools that allow optimizing an image for web publishing - resizing and significantly reducing the size without visibly changing the image (to human eyes).  It is fairly common to reduce a 300K jpg image to 50K this way - same resolution, looks the same, just smaller. **convert** is the tool for that and easily scripted.

Why bother with this?  If creating how-to guides, having a smaller image will mean everything is faster. There's less to load.

---

### Post by vasa1 on 2014-09-11
OP may not have **scrot** by default because it's Ubuntu minimal + Openbox. I have scrot because it comes with Lubuntu. Scrot does have a quality setting taking values from 1 to 100, 100 being the best and 75 being default. BTW, I'm not sure that scrot is being actively developed :(

I don't work with images except for uploading screenshots when asking for help or to illustrate a point. But for people who work a lot with images, imagemagick would be invaluable. I also appreciate the point of not using high quality images needlessly.

---

