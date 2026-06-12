---
title: "Flash freezes when settings window opens"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by milton0523 on 2012-07-24
When I'm playing a game online, and it asks me to let it store information n my computer, I can't press anything on the dialogue box. Same thing when i right click and press settings. I have ubuntu 12.04.

---

### Post by NikTh on 2012-07-24
Hi , 
yes maybe you have right.. flash its a bug .. sometimes. 
I am not really sure if this have something to do with your video card (driver) , or exclusively with flash player. 

You can do your job with another way. 
open a terminal (ctrl+alt+t) 
and give these commands ```
sudo apt-get install adobe-flash-properties-gtk
flash-player-properties
```second command will open a window and you can change your preferences from there.

Thanks

---

### Post by milton0523 on 2012-07-24
That helps, but doesn't solve my problem. It just lets me decide if i want to allow a site or not, but my problem is flash asking to store more info than currently allowed. Thanks, but that still didn't work.

---

