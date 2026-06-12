---
title: "System Sounds !!!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by ENigma885 on 2008-05-10
After an upgrade from 7.10 to 8.04 i couldn't enable system sounds-but the media sounds r working well- (System>>Preferences>>Sound> Sounds Tab)..i faced the same problem in 7.10 but i got it to work after installing those packages 
```
sudo apt-get mpg123 mpg123-alsa esound
```
when i tried to do the same thing in Hardy Heron and i rebooted my system,*_GNOME panels weren't loaded properly_* and the system in general didn't response . 
So i booted up in safe mode and uninstalled the previously installed packages and after several tries i figured out that *_(esound) is the reason behind this problem._*

***[COLOR="Red"]so is there any way to enable the system sounds or to configure esounds not to crash my system at start up?[/COLOR]***

btw after uninstalling esound ,sounds preview in (System>>Preferences>>Sound> Sounds Tab) doesn't work. and i tried to play the files in Audacious and they worked .

---

### Post by joshsmith on 2008-05-10
make sure enable software mixing is enabled in System>>Preferences>>Sound> Sounds Tab
you dont want to install esound, or those other packages anymore

new sound server in hardy: my thread may be of some  help: 
[http://ubuntuforums.org/showthread.php?p=4725430](http://ubuntuforums.org/showthread.php?p=4725430)

---

