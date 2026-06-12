---
title: "Cannot switch to SU in Ubuntu 15.10"
date: 2016-01-19
forum: New to Ubuntu
---

### Post by joan7 on 2016-01-19
I am still working on getting Ubuntu 15.10 running to my liking.
In my effort to change my wallpaper, I have tried to load a file into /usr/share/backgrounds/ but I am denied access.
I have tried to open a terminal window and move the file manually from there but still cannot get access.
I have tried to log-in as SU but it is not accepting my password.

Can anybody tell me where I am going wrong , or what I am missing here ?
thx,
-J

---

### Post by howefield on 2016-01-19
Precede the terminal command with sudo, eg

```
sudo cp /home/user/Pictures/picture.jpg /usr/share/backgrounds/
```

You'll be asked for your password (which won't be shown as you type it, then press enter.

---

### Post by grahammechanical on 2016-01-19
In System Settings>Appearance we can direct Ubuntu to use an image in the Pictures folder as background wallpaper. We change the panel above the box that shows all the wallpapers from "Wallpapers" to "Pictures."

I do not think that simply putting an image file in /usr/share/backgrounds/ will be enough to make that image appear in the Appearance utility as a selectable background image. We have to also edit /usr/share/gnome-background-properties/wily-wallpapers.xml and follow this pattern
> 
<wallpaper>
     <name>Tramonto a Scalea</name>
     <filename>/usr/share/backgrounds/Tramonto_a_Scalea_by_Renatvs88.jpg</filename>
     <options>zoom</options>
     <pcolor>#000000</pcolor>
     <scolor>#000000</scolor>
     <shade_type>solid</shade_type>
 </wallpaper>

If using Gedit it will make a backup copy of the file but it will hide the file by putting ~ in front of the file name. This back up copy will still be read and so you will find that there appears a duplicate listing of wallpapers.

Much simpler to stick the image in the Pictures folder.

Regards.

---

### Post by joan7 on 2016-01-19
Hi guys,
thank you both for your informative replies.
I used the sudo command and it worked a treat. I copied my picture over and then rt clicked on the Desktop -> Change desktop background, and loaded my image.
OK, as you say GrahamM. the image was not there immediately, but I found it under the tab " appearance". it was then just a simple case of loading it. i will look a bit closer at the solution that you suggest, just in case I need to go through this again.
Thx,
-J

---

