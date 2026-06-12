---
title: "[SOLVED] Install .ttf fonts in xubuntu?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by tstack77 on 2008-05-17
I downloaded the segoe font and attempted to install it by making a .font folder in \home, didn't work.

How is this done in xubuntu?

---

### Post by shadow-of-sin on 2008-05-17
In normal Ubuntu you have to run the following command in the terminal after copying the font to ~/.fonts/:
```
sudo fc-cache -f
```

I think it is the same for xubuntu.

---

### Post by tstack77 on 2008-05-17
That did it!

Thanks

---

### Post by terryman007 on 2010-03-19
Great! it´s easy, almost as easy as pie.... first, I suggest downloading/copying all fonts, such as ttf to the same folder.  Then, 
```
sudo thunar
```
:shock:.  Then open your new fonts folder and COPY all fonts you want to paste to
```
/usr/share/fonts/truetype
``` (I used truetype folder because that´s the kind of font I copied.)  Then PASTE the new fonts.  Close THUNAR.
Last step is go back to TERMINAL and type
```
sudo fc-cache -f
```

---

### Post by georgelappies on 2011-04-25
> **terryman007 said:**
> Great! it´s easy, almost as easy as pie.... first, I suggest downloading/copying all fonts, such as ttf to the same folder.  Then, 
```
sudo thunar
```
:shock:.  Then open your new fonts folder and COPY all fonts you want to paste to
```
/usr/share/fonts/truetype
``` (I used truetype folder because that´s the kind of font I copied.)  Then PASTE the new fonts.  Close THUNAR.
Last step is go back to TERMINAL and type
```
sudo fc-cache -f
```

Excellent, thanks this helped me on xubuntu 11.04 as well! :)

---

