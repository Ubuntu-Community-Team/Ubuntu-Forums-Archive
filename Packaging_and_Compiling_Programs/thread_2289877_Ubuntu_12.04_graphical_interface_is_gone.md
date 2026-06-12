---
title: "Ubuntu 12.04 graphical interface is gone"
date: 2015-08-07
forum: Packaging and Compiling Programs
---

### Post by mrigendra-chaubey on 2015-08-07
[COLOR=#111111][FONT=Ubuntu]I was trying to set up my build environment for beagleboneblack.I was following standard instructions from this site[/FONT][/COLOR]
    [https://source.android.com/source/initializing.html](https://source.android.com/source/initializing.html)
[COLOR=#111111][FONT=Ubuntu]I was installing required packages one by one. Now after reboot, GUI is gone. It is giving a message with some options that I can't select through keyboard or mouse. Doing a escape takes me to a CLI. I tried this[/FONT][/COLOR]
 sudo services lightdm start
[COLOR=#111111][FONT=Ubuntu]and[/FONT][/COLOR]
 sudo startx
[COLOR=#111111][FONT=Ubuntu]but nothing happens.I remember while installing this one[/FONT][/COLOR]
  libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386
[COLOR=#111111][FONT=Ubuntu]or this one[/FONT][/COLOR]
  libgl1-mesa-dev g++-multilib mingw32 tofrodos
[COLOR=#111111][FONT=Ubuntu]It was removing x server things then again setting up. What can I do now? P.S. Also while installing libgl1-mesa-glx, it said something like this[/FONT][/COLOR]
  The following packages have unmet dependencies:
  libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 8.0.4-0ubuntu0.4)
  Recommends: libgl1-mesa-dri:i386 (>= 7.2)
[COLOR=#111111][FONT=Ubuntu]So I did this[/FONT][/COLOR]
 sudo apt-get install libgl1-mesa-dri

---

