---
title: "Personal image for login screen"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by LustyCrow on 2012-01-22
Apologises if this question has been asked but I couldn't find the thread for it.
I'm running Ubuntu 11.10 and am trying to change the background picture, on the login screen, from /usr/share/backgrounds/warty-final-ubuntu.png to one of my pictures. 
So far I've used this command:
 
[COLOR="Red"]cp -v /home/Ubuntu/Pictures/My?Bass.png /usr/share/backgrounds/My?Bass.png [/COLOR]

Then:

[COLOR="Red"]sudo gedit /etc/lightdm/unity-greeter.conf[/COLOR]

And change:

[COLOR="red"]background=/usr/share/backgrounds/warty-final-ubuntu.png[/COLOR]

To:

[COLOR="red"]background=/usr/share/backgrounds/My?Bass.png[/COLOR]

But when I restart I'm just getting a blank background. (Still, preferable to the one it comes with.) 
Thanks for any help that can be offered. :)

---

### Post by collisionystm on 2012-01-22
download 

ubuntu tweak

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by LustyCrow on 2012-01-22
Cool, thanks. :)

---

### Post by Double.J on 2012-01-22
For future reference, the method you were using was technically correct - the .png file may have just been too large; camera photo's can be int he range of a hundred Mb, the background images used by lightdm are in the Kb size - My personal image is 1.1Mb :)

All the best ;)

---

