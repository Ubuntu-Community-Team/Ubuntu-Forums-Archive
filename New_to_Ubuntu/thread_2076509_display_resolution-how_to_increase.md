---
title: "display resolution-how to increase"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-10-26
i m finding max display resolution in my system settings - display as 1280x800...a few less resolution options are available but nothing more than 1200... i want to go for something like 1600x1200,,, how can i get that????presently resolution is less hence desktop icons are very large...plz guide

---

### Post by Paari on 2012-10-26
SETTINGS >> DISPLAYS >> RESOLUTION... U'll have a drop down List box there. U can choose from...
If you are sure that the list doesn't have your screen's maximum resolution, that your system used to support, then try updating your video card driver, if you have one... :)
You can find your video card by using the command below...
```

lspci

```And depending on your Garaphic card, the following link will be useful. Check it out...:D

[URL="http://<br /> http://ubuntu.wikia.com/wiki/Update_Graphic_Drivers<br />"]http://ubuntu.wikia.com/wiki/Update_Graphic_Drivers
[/URL]

---

### Post by syednasirraza on 2012-10-26
thnx paari for reply
this is detail of my vga card,,(obtained by lspci comand)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
now  how can i come to know if it requires any updation or not??? and if  requires updation??how to go for it????can u plz explain step wise....

---

### Post by Paari on 2012-10-27
Install mesa-utils by running the following code. 
```

sudo apt-get update
sudo apt-get install mesa-utils

```

You can also do it if u have synaptic manager by running a simple search. After  installed, your video card will be detected by your ubuntu...

Check if the resolutions changed...:)

No?  Then i've googled and found the repository which holds the drivers for  your graphic card. You can have a look at it(May be useful if mine  doesn't work, u can try another one of your choice)  [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

Type in the following code... This one is for intel GL drivers
```

git://anongit.freedesktop.org/git/mesa/mesa

```

Update again.... Any Progress please post back.... You are always Welcome :)

Regards,
Paari

---

### Post by syednasirraza on 2012-10-28
i updated and then installed mesa-utils...intstallation went fine, fol is the output,,,yet did not find anything new in resolution place...dont knwo why

:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) precise/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 9s (2,842 B/s)     
Selecting previously unselected package mesa-utils.
(Reading database ... 229160 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...

---

### Post by El Tito on 2012-10-28
Have you tried in the console:

xrandr -q

this will list the monitors plugged and their resolutions.
After that, you can set manually the resolution of the chosen monitor with:

xrandr --output thenameofyourdisplay --mode resolution
for example:
xrandr --output VGA1 --mode 1366x768

Hope this helps!!

---

### Post by syednasirraza on 2012-10-30
thanks eltito for reply.....
here under is the output of xrandr,...the max prefered option shown is 1280x800...does it mean i will not be able to go beyond/above this????is it limitation of my screen.vga card???


nasir@NASIR:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

---

### Post by El Tito on 2012-11-10
Sorry for the delay, I've been a little busy.
If there are no more display modes and you are sure your monitor supports more,
then it might be due to the graphic card module (driver).

But before you can try the following link:
*[COLOR=Blue]http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html[/COLOR]*
 
Good luck!

---

### Post by syednasirraza on 2012-11-11
thnx el titio for replying... im not finding anymore options,,nor i m sure if my monitor supports more...

---

### Post by El Tito on 2012-11-11
In theory, with the link that I posted above, you can add new resolutions. 
Have you followed the steps explained there?, and read the comments after the explanation in that link!! (personal advice based on personal experiences) I learned that the hard way, sometimes something doesn't work and somebody in the comments gives further insight or even the solution.

If that doesn't work, I'll be running out of options...

Hope this helps.

---

