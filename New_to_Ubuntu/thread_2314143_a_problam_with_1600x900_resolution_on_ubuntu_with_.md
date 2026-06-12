---
title: "a problam with 1600x900 resolution on ubuntu with all graphic card"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by Jalal_Alizadeh on 2016-02-18
hi . i have a problem with 1600x900 resolution .  that is on bellow pic . how can i fix this . i tested all ways and i can't fix this problem .


[IMG]http://i.stack.imgur.com/8xp9V.jpg[/IMG]

---

### Post by ajgreeny on 2016-02-18
What output do you get from command **xrandr**?

---

### Post by Jalal_Alizadeh on 2016-02-19
cvt 1600 900 60
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

-------------------

xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

xrandr --addmode VGA-1 1600x900_60.00

xrandr --output VGA-1 --mode 1600x900_60.00

---

### Post by SeijiSensei on 2016-02-19
What kind of display is this?  A computer monitor or a TV?  If the latter, you may need to play with its aspect ratio settings.

---

### Post by ajgreeny on 2016-02-19
Assuming your resolution requirement of 1600x900 is correct for your monitor, that is what your graphic card is giving you, and as SeijiSensei says, you may need to play around with the monitor or TV settings to make sure it is set correctly for that resolution.

---

### Post by Jalal_Alizadeh on 2016-02-19
thanks . but of 2 years ago i test with some graphic card and all time i could not make true resolution and change ubuntu to windows . i use of samsung syncmaster 2033 and now my graphic is nvidia gtx 650 .
there is special problem .

---

### Post by SeijiSensei on 2016-02-19
Are you using the proprietary NVIDIA driver? If not, give that a shot.

---

### Post by Jalal_Alizadeh on 2016-03-08
sorry for my late answer . i was in travel .
after install nvidia current ... i used of all proprietary NVIDIA driver and i checked all radio button . but problem no fixed .
i think this is a problem about my monitor .
i will change my monitor and after it , if i find a problem , i will post another topic .
thanks very much .

---

