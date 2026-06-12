---
title: "Switching position of buttons"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Vladimir Pavic on 2012-12-25
Dear friends, 

Is there any possible way I could switch the position of buttons on the top of the screen? I want to have minimise/maximise/close buttons on the right side and the rest of the commands on the left, as I have shown on the attached picture (which I manipulated by GIMP).

Thank you.

---

### Post by TOMBSTONEV2 on 2012-12-25
Perhaps this will help, if not I'll try to figure something out for you.

[http://www.lubuntutips.com/2012/07/moving-close-maximize-and-minimize.html#.UNk1dflx0y0](http://www.lubuntutips.com/2012/07/moving-close-maximize-and-minimize.html#.UNk1dflx0y0)

---

### Post by Vladimir Pavic on 2012-12-25
Hm. This may work in Lubuntu, but I have Ubuntu 12.04.

---

### Post by vasa1 on 2012-12-25
> **Vladimir Pavic said:**
> Hm. This may work in Lubuntu, but I have Ubuntu 12.04.
But your post has been tagged as Lubuntu :) hence the confusion.

IMO, it's a forum bug because it happens quite often.

---

### Post by vasa1 on 2012-12-25
And, with reference to your image, it is possible in Ubuntu to switch the min/max/close buttons around but I don't think you'll be able to move the other ones, the panel icons, at all.

---

### Post by lisati on 2012-12-25
> **Vladimir Pavic said:**
> Hm. This may work in Lubuntu, but I have Ubuntu 12.04.

I have removed the "lubuntu" tag for you.

---

### Post by TOMBSTONEV2 on 2012-12-25
For ubuntu 12.04; There is a tool called ubuntu tweak, that does this. 

To install ubuntu tweak in 12.04:
In terminal paste/type
```
sudo add-apt-repository ppa:tualatrix/ppa
```Followed by```
sudo apt-get update
```And finally
```
sudo apt-get install ubuntu-tweak
```For ubuntu 12.10 you can use this command to switch the buttons:
In terminal type:

```
gsettings set org.gnome.desktop.wm.preferences button-layout  ':minimize,maximize,close'
```A program called dconf-editor will  achieve this in 12.10 to install it open the software centre and search  dconf. Then select dconf Editor > install it.
(I added this for the 12.10 users who may come across this)

---

### Post by Vladimir Pavic on 2012-12-25
I have got Ubuntu Tweak. So, what exactly am I supposed to do?
Never mind the panel icons. If I could move max/min/close buttrons to the right - that would be great!

---

### Post by zombifier25 on 2012-12-25
You can't actually modify the Unity panel, but you can modify the buttons on the title bar.

Open Ubuntu Tweak, go to Tweaks > Windows, then choose "Right".

---

### Post by Vladimir Pavic on 2012-12-25
Thank you (and others). It works!

---

