---
title: "Loading Images/Pictures from Disk using XLIB"
date: 2012-02-22
forum: Programming Talk
---

### Post by yank3s on 2012-02-22
Hello Community,

I am developing a project using Xlib with C++. What I am focused on doing now, after successfully implemented some basic operations, is to load a PNG image from disk into the window. I've been searching the web and I can't really find something that could explain how can i load an image from the disk into my window. I've seen how to load a .xbm file, but unfortunately, converting png to xbm loses A LOT of quality on image. The other option I've thought about, was to convert png to xpm (X Pixmap). However I don't know either how can I load a XPM from disk into my project window.

Does anyone have a clue on how to load a PNG or XPM image into the window?

Thank you very much in advance.

EDIT: It is solved. I did the following:


   Pixmap pix = XCreatePixmap(display, RootWindow(display, screen), width, height, DefaultDepth(display, screen));

   XImage* ximg = XCreateImage(display, CopyFromParent, 24, ZPixmap, 0, (char*)img_bits, width , height, 32, width*4);
   XPutImage(display, pix, DefaultGC(display, screen), ximg, 0, 0, 0, 0, width, height);

and then just used CopyArea to copy from pixmap to the window. I used libpng to read pixels from a png file.

---

### Post by yank3s on 2012-02-22
Hey there.

OK, so I managed to find this libpng in order to get info about pixels on the PNG image. So i fill a char array with the RGB value of each pixel. 
```

    Pixmap pix = XCreatePixmap(display, RootWindow(display, screen), 800, 600, DefaultDepth(display, screen));
    pix = XCreateBitmapFromData (display, RootWindow(display, screen), (char*)img_bits, 800, 600);
```

The image i read the information about the pixels is also 800x600 pixels.

However, in the Expose Event case, when I am doing :
XCopyArea(display, pix, window, DefaultGC(display, screen), 0, 0, 800, 600,  0, 0);

I am getting the following message:
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  62 (X_CopyArea)
  Serial number of failed request:  19
  Current serial number in output stream:  19

Why is he failing on this CopyArea thing ?

Thank you very much in advance.

---

