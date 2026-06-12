---
title: "No sound at log in or log out?"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by vasa1 on 2012-11-09
Does anyone know how to have sounds, drum-rolls, or whatever, play at the time of log in or start up?
I have a standard Lubuntu 12.10 set-up and can play music, videos etc without issue.

---

### Post by Rex Bouwense on 2012-11-09
Sorry for the late reply but I only get on when I can.  I knew that this was possible since I had posted on an earlier thread with the same subject.  It eventually had a solution.  See this site:
[http://ubuntuforums.org/showthread.php?t=1917685&page=2](http://ubuntuforums.org/showthread.php?t=1917685&page=2)
Post number 12 specifically has an answer.  I never did test it and it was for Lubuntu 12.04.

---

### Post by vasa1 on 2012-11-12
Rex, thanks for your post. I will check it out and post back.

---

### Post by vasa1 on 2012-11-12
Doesn't work for me!
```
[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/**gnome-mplayer** /home/vasa1/.config/autostart/desktop-login.ogg
```
I tried both mplayer and gnome-mplayer and I have a functional little ogg file in the autostart folder.

---

### Post by blade4 on 2012-11-12
Try downloading ubuntu tweak and changing the login settings from there . 

Goto : [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Hope this helps .

---

