---
title: "Mini Guide: Compiz Checker"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by skymera on 2008-05-07
I found this script on another website.
Basically it checks whether Compiz can run. Great!

Simply make the file executeable, and run from the terminal.

I ran and here's my output:
```

scott@scott-desktop:~/Desktop$ chmod +x compiz-check.xps 
scott@scott-desktop:~/Desktop$ ./compiz-check.xps 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

scott@scott-desktop:~/Desktop$ 

```

Easy!
I attached the script if you want to try it.

---

