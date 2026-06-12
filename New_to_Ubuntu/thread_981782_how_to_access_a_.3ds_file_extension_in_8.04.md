---
title: "how to access a .3ds file extension in 8.04"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2008-11-14
hi techies....

i have installed a .3ds extension file of a design of space shuttle from [www.nasa.gov](www.nasa.gov).

but i am unable to open it in my ubuntu 8.04.

plzz can anybody help me out.

i also tried to install G3Dviewer . but as i downloaded it in .tar.gz extension so i need a proper steps to install... 
i need  that too... !!!   :-(

thanking you in advance for an early help/\..

---

### Post by talsemgeest on 2008-11-14
Unfortunately it could have been made in any number of 3d applications.

However, you might want to give blender a go, to see if that will open it. ```
sudo apt-get install blender
```

As for your .tar.gz program, .tar.gz is just an archive, like .zip in windows. You need to see what is inside it, so to extract it, right-click it and click "extract here".
Take a look inside, and if it has files like "install" and "configure", then you should follow the tutorial [here](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

### Post by jlbr21 on 2008-11-14
That file is surely a 3DS MAX file and, unfotunately there is no 3DS max for Linux (or Mac), but as suggested, install Blender and try to import it into that program, if you want to render the file, then you might want to try downloading a render program such as Lux (luxrender.net/)or Yafray (yayray.org) and there are more actually, google "open source render programs" and see what you can find, and then you could try to render the file from any of those programs.

---

### Post by shreyanshjain8 on 2008-11-14
thanx everybody ...

iam trying to install blender...


thanks once again for your valuable time..

---

### Post by MenZa on 2008-11-14
Blender will work well if you just import the file. I've done this a hundred times developing games. :)

---

