---
title: "Instaling fonts"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by kkira13 on 2013-01-16
Hello, I am trying to install fonts on Xubuntu, but it seems just not to work. I tried this 

> sudo thunar
Then open your new fonts folder and COPY all fonts you want to paste to

/usr/share/fonts/truetype

 Then PASTE the new fonts. Close THUNAR.

 Last step is go back to TERMINAL and type


sudo fc-cache -f

it didn't work. I realized that I don't have msfonts installer included in restricted extras so I installed it and repeated the procedure, however it's still not working. Any suggestions ?

---

### Post by slickymaster on 2013-01-16
After copying the new fonts to **/usr/share/fonts/truetype**, in order to re-build the font cache, try ```
sudo fc-cache -f -v
``` instead of sudo fc-cache -f.

After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs. However, some programs may require you to log out and log back in.

---

### Post by mastablasta on 2013-01-16
sudo thunar
^
^
|
Never use sudo with graphical applications. it is just calling for trouble. here is a good explanaiton why: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by slickymaster on 2013-01-16
> **mastablasta said:**
> sudo thunar
^
^
|
Never use sudo with graphical applications. it is just calling for trouble. here is a good explanaiton why: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You are completely right and that is a mistake that I continually persist in practice (mostly by distraction).

---

### Post by kkira13 on 2013-01-17
> **slickymaster said:**
> After copying the new fonts to **/usr/share/fonts/truetype**, in order to re-build the font cache, try ```
sudo fc-cache -f -v
``` instead of sudo fc-cache -f.

After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs. However, some programs may require you to log out and log back in.

Thank you, this worked fine.

---

