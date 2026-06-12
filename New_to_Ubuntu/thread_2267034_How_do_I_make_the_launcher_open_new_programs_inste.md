---
title: "How do I make the launcher open new programs instead of switch to opened ones?"
date: 2015-02-26
forum: New to Ubuntu
---

### Post by jakebuscher on 2015-02-26
Hello Ubuntu comunity! 

I am trying to fiigure out how to make the launch bar launch a new program instead of bringing me to an already opened program. This is very frusturationg when I am on a workspace and I just want to open the calculator of something and all of a sudden it brings me to some other workspace. I searched around and can't find any way to change this. 

Thanks in advance

---

### Post by CantankRus on 2015-02-26
Use middle click to launch a new instance of an application.

---

### Post by jakebuscher on 2015-02-26
I only have two buttons on my laptop.

---

### Post by CantankRus on 2015-02-27
I have never used a laptop but I believe you can simulate a middle click
by simultaneous left and right click.

You may have to run this command first ....
```
gsettings set org.gnome.settings-daemon.peripherals.mouse middle-button-enabled true
```

---

### Post by jakebuscher on 2015-02-27
Wow I never knew that, it seems to work, thanks! Anyway to get them to launch with only a lift click?

---

### Post by Frogs Hair on 2015-02-27
Right clicking the launcher icon and selecting open in a new window will allow for a new instance of a program in a different workspace in many cases. However,not all programs have this option.

---

### Post by Jakey_TheSnake on 2015-02-27
The Gnome Tweak Tool has nice 'extensions' support - one of the bundled ones is "Launch New Instance" - *Always launch a new instance when clicking in the dash or the application view.* Simply move the slider to the 'ON' position. [[Image]("http://i.imgur.com/DTPMM6D.png")]

I have no idea whether you're using unity, or if it has an equivalent, but Gnome Shell is so much nicer anyway ;)

---

