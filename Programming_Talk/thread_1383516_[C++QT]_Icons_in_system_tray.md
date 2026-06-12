---
title: "[C++/QT] Icons in system tray?"
date: 2010-01-17
forum: Programming Talk
---

### Post by supershin on 2010-01-17
I'm editing a program which uses C++ and QT and I want to put my own icon in place of another. 

Currently the line is ```

#define IMG_TOR_STOPPED    ":/images/22x22/tor-off.png"
```

All the icons are in a folder called res so I place my icon in there too and change the name of the image file in that line. So now I have

```
#define IMG_TOR_STOPPED    ":/images/22x22/my-icon.png"
```

Thing is when I compile and run there is no icon on the system tray, just a blank space. The image I'm using is a 22x22 png, same as the image currently used. Also there is no images folder. I even changed the path to "~/res/22x22/my-icon.png but it doesn't work. 

I don't know what I'm doing wrong or not doing, can someone help me?

---

### Post by supershin on 2010-01-20
Bump.

---

