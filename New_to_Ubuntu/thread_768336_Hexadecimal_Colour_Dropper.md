---
title: "Hexadecimal Colour Dropper"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by saj0577 on 2008-04-26
Does anyone know a program or a way of making one that has a simple dropper which when you click on a pixel it tells you that pixels hexadecimal code.

Bit like the dropper function in this dialogue of gimp.

Saj

---

### Post by opscure on 2008-11-26
yep.  open a terminal and type:
```
kdialog --getcolor
```
if you don't have kdialog installed you may need to do a:
```
sudo apt-get install kdialog
```
cheers.

you can use this in a script as well by setting this command to a variable, so:

```

#!/bin/sh
myColor=`kdialog --getcolor`
if [ "$myColor" = "#000000" ] 
then
kdialog --msgbox "Your color is black"
else
kdialog --msgbox $myColor
fi

```

---

### Post by jpoRS on 2008-11-26
Depending on what you need, System>Preferences>Appearences, Background tab, Click on the little color square, and a dropper tool comes up.

I guess this isn't really helpful if you need to find the color of things often, but if it is just a once and done thing, you don't need to install anything.

Good luck!
jim

---

### Post by jimv on 2008-11-26
If this isn't something you need to do often, you can take a screenshot of whatever you're looking at and open it with the GIMP.

---

### Post by jpoRS on 2008-12-04
OoOoo!!! I just found the program you are looking for!

```
sudo apt-get install gcolor2
```

Good luck!
jim

---

