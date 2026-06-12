---
title: "How To Move A Number Of Files To Usr Folder At Same Time?"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by unknowngal on 2012-09-22
Hello! I'm kind of stuck here. See, I wanted to move individual script files into the GIMP scripts folder. At first, I wasn't able to, it was giving me an access denied type of thing. I surfed around and found something to input into the terminal to allow me to move the folder the scripts were in into the GIMP scripts folder. But it turns out that I had to move the _individual files_ for them to show in GIMP. How do I do that? (I would like to move them all instead of one by one, they're quite a few.) And then, how do I delete the folder I moved in there (since I don't need it)?

Thank you!!

---

### Post by TenPlus1 on 2012-09-22
It sounds like you are trying to move script files inside the filesystem which is protected and you need root permissions to do so...

You can make this easy by typing this in Terminal for a root access filemanager:

sudo nautilus

or if you use xubuntu:

sudo thunar

or even Lubuntu:

sudo pcmanfm

then use the window that appears to copy the files you need, be careful though as it is a root access file manager window and can delete important stuff...

---

### Post by jerrrys on 2012-09-22
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=move+multiple+files&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=move+multiple+files&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by unknowngal on 2012-09-22
Thank you, TenPlus1! That did it! :) And thank you jerrrys, I'll have to use the search option too next time!

---

### Post by Cheesemill on 2012-09-22
> **TenPlus1 said:**
> It sounds like you are trying to move script files inside the filesystem which is protected and you need root permissions to do so...

You can make this easy by typing this in Terminal for a root access filemanager:

sudo nautilus

or if you use xubuntu:

sudo thunar

or even Lubuntu:

sudo pcmanfm

then use the window that appears to copy the files you need, be careful though as it is a root access file manager window and can delete important stuff...
Just a quick note - You shouldn't use sudo to run graphical applications, you should always use gksudo instead.
Using sudo can cause lots of seemingly unrelated problems with your system.

---

### Post by StinkySQL on 2012-09-22
Handy trick. I'll use that some day.

---

