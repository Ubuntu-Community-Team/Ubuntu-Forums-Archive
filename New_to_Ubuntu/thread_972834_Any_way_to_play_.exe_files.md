---
title: "Any way to play .exe files?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by michael91 on 2008-11-06
Any help would be greatly appreciated.

---

### Post by lisati on 2008-11-06
Yes - the program you need is called "WINE".

See here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by michael91 on 2008-11-06
I thought that I would need that, but I've forgotten how to use it. Could you please briefly explain?

---

### Post by lisati on 2008-11-06
> **michael91 said:**
> I thought that I would need that, but I've forgotten how to use it. Could you please briefly explain?

I haven't used it in a long time.
See here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by Poyntz on 2008-11-06
> **michael91 said:**
> I thought that I would need that, but I've forgotten how to use it. Could you please briefly explain?

simple. open up the directory where your exe file is using cd <path here> in shell. then type **wine <filename>.exe**. If it's a wine emulator compatible .exe file it will open. Else you may need to install wine tricks.
To install it type in shell: wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)  
To use it type in shell: sh winetricks    
For additional info: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Hope this helps

---

