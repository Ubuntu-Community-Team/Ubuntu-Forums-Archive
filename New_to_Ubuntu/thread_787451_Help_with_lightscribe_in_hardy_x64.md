---
title: "Help with lightscribe in hardy x64"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by famous3warriors on 2008-05-08
Hello can some one please help with this light scribe problem that I am having.  I downloaded from the lightscribe.deb file both and the simple labler.  But for some reason my liblightscirbe.so and so1 is broken.  Is there and older deb file that I could download and use so I could get this thing working.  Thanks I really do appreciate it.

---

### Post by famous3warriors on 2008-05-08
Here are the some of the files I have to help.

---

### Post by GreatGariny on 2008-05-27
I compiled a guide on getting lightscribe and 4L working on Hardy Heron x64.

[http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html](http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html)

If you already have the deb files installed you can try running:
```
sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/
sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/
sudo ldconfig
```

Then run the 4L program:
```
sudo 4L-gui
```

---

