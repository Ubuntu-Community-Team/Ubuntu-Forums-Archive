---
title: "Efficient lightweight alternative to Ghisler Total Commander?"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by honeybear on 2011-10-07
Hello,

Krusader is the best. However KDE is kinda heavy, requiring lot of memory, for some of you.

For some that like it lightweight, what would you advice as an efficient lightweight alternative to Ghisler Total Commander? 

Thanks

---

### Post by Lars Noodén on 2011-10-07
I'm assuming that's a file manager or something.  You have some choices for file managers:

Dolphin
Konqueror
Thunar
Krusader
Xfe
ROX-Filer
Midnight Commander

Some include support for remote file access using SFTP.

You can try several and decide which is light enough.  My guess would be Thunar or Xfe.

---

### Post by WasMeHere on 2011-10-07
In the beginning of my linux experience I ran Ghisler's Total Commander via *Wine*, so until you find something satisfactory, that is an option. I also tried Midnight Commander, but it feels outdated.

As a matter of fact, I use *Nautilus* which is called by *Places* in the menu system. Once you learn all the possibilities it is quite nice.

Some Good-to-know tips: *F2*-rename, *F3*-two panels
*Drag and drop* a directory or file icon *into a terminal window*, and you have its full path there.
and *nautilus-open-terminal*:
> **lazyart said:**
> 

It's not an app but a nautilus plug-in.  ```
sudo apt-get install nautilus-open-terminal
killall nautilus
```(the second line is necessary to restart nautilus and make the plug-in work.)
Right click on an empty area in nautilus and you'll have the option to open the terminal from that directory.

Have fun
Olle

*Edit: Lightweight: +1 for Thunar*

---

