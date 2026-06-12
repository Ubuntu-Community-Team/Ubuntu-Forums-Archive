---
title: "[SOLVED] How to add new fonts"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ellalan on 2008-04-28
Hi
Could some one tell me how to add new fonts in Hardy. Thanks.

---

### Post by DezSP on 2008-04-28
There's a fair number of fonts available as packages in the repository. Did you have something specific in mind?

---

### Post by tandkzy on 2008-04-28
It's easy to install a truetype font.
Just copy you truetype font into /usr/share/fonts/truetype/.

---

### Post by kpkeerthi on 2008-04-28
1. Make a folder .fonts under your HOME directory. Yes it is a hidden folder beginning with a **dot**.
2. Copy the font files (TTF?) to $HOME/.fonts using nautilus.
3. Refresh the font cache. Open a terminal window and then run this command
```
fc-cache -fv
```
Your fonts are ready to be used.

---

### Post by ellalan on 2008-04-28
Thank you guys for the quick response, but I am unable copy my font using nautilus,
the error message says" this action not supported in nautilus".
I have tried all suggestions,if you find any solutions please let me know. Thank you.

---

### Post by redbob on 2008-04-28
Any operation with Nautilus that envolves system, is better if you open by gksu > gksu nautilusdue to permissions issue. Look, I found a page telling how to install M$ true type fonts. [http://corefonts.sourceforge.net, but the easiest way to do it is typing> sudo apt-get install msttcorefonts/](http://corefonts.sourceforge.net, but the easiest way to do it is typing> sudo apt-get install msttcorefonts/)

---

### Post by redbob on 2008-04-28
But the better way to install them is typing in terminal> sudo apt-get install msttcorefonts

---

### Post by ellalan on 2008-04-28
Thank you DezSP, I got my font from Synaptic and everything fine.

---

