---
title: "Black bars appearing on sides of screen"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by heema-d on 2012-07-16
I have been using Ubuntu for a little over a month now and most my problems can be solved by looking on this forum. 

I have ran into a problem that I cannot solve. I have downloaded the whole Marathon Trilogy(AlephOne)and each time I close out of the game my screen becomes smaller, the icons become enlarged, and black bars appear on the sides of the screen.

Any help would be appreciated, thanks.

---

### Post by NikTh on 2012-07-16
Hi , 
your problem sounds like the game affects screen resolution system-wide. If this is the problem i think only developers of the game (or their forums) can help you. 

I can only tell you that you can resume your resolution with xrandr . Open terminal (ctrl+alt+t) and write ```
xrandr
``` the output it will be your card's supporting resolutions , you can change the resolution with this command 
```
xrandr --output VGA1 --mode <resolution> 
```VGA1 may change depend on desktop or laptop 
and resolution = one from xrandr's list. 
If you want help post the output of xrandr here { inside [CODE] tags , by highlighting the text and click at # symbol on top of message pane}
Thanks

---

