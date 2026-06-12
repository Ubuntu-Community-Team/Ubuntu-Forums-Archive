---
title: "Openoffice  can not change font size on text file"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by zeelog on 2012-08-18
I can not get Openoffice to change the font size on an 
 imported text file. I keep getting font size 10 when I
 want it changed to 20. I tried changing the font type
 and it wouldn't do that either. So I saved it as an .odt
 file, loaded the .odt file, and tried again. Openoffice
 doesn't do anything.  Do I have a crippled version of
 Openoffice ?  I'm using Ubuntu 11.04

---

### Post by llamabr on 2012-08-18
beats me.  We'd probably need to see an error log, or at least a screen shot.

In the meantime, as a work around, try ctrl-a, ctrl-n, ctrl-v, and then try to change the font.

---

### Post by duncan12 on 2012-08-18
If you're using OpenOffice, try LibreOffice instead. It's based on the same source code and can open the same file type fine, but has been developed on much more recently and is more stable.

```
sudo apt-get install libreoffice
```
will do it. Then open that file with LibreOffice instead.

---

