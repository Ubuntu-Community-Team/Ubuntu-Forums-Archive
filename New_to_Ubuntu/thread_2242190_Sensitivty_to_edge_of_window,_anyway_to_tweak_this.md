---
title: "Sensitivty to edge of window, anyway to tweak this?"
date: 2014-08-31
forum: New to Ubuntu
---

### Post by cwmoser on 2014-08-31
When resizing a window, is there anyway to adjust the sensitivity
along the verticle edges?  With my system, its difficult to get the mouse
to change from a pointer to an edge indicator when I want to resize.
I would like for sensitivity area to be larger.

Carl

---

### Post by CantankRus on 2014-08-31
I believe this is a setting which differs according to your gtk theme.
However in 14.04, the drawing of window decorations 
is now done by unity and gives a generous grab area.

---

### Post by cwmoser on 2014-09-02
Found a solution that works:

Resize Window Border too small to grab with mouse
sudo  gedit   /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml  
Set the following values in **frame_geometry_normal** as desired:
<distance name="left_width" value="5"/>
<distance name="right_width" value="5"/>
<distance name="bottom_height" value="5"/> 

I set all three on mine to 5

Carl

---

