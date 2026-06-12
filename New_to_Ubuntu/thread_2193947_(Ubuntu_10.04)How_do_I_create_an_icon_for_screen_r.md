---
title: "(Ubuntu 10.04)How do I create an icon for screen rotate?"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by winslowevan2 on 2013-12-15
I have a tablet PC I bought for reading PDFs and it has no keyboard so I can't bind keys easily. I want to create a desktop icon so that I can rotate 90 degrees each press. Thanks!

---

### Post by asus-user on 2013-12-15
> **winslowevan2 said:**
> I have a tablet PC I bought for reading PDFs and it has no keyboard so I can't bind keys easily. I want to create a desktop icon so that I can rotate 90 degrees each press. Thanks!

I will keep looking for a way to write a program in bash to do all rotations in one file :) .
In the mean time I could help you to create executable files (multiple ones) to "rotate left", "rotate right", "rotate 180 degree", "rotate back to normal".
The steps are:
1- in Terminal:
```
xrandr
```
look at the output of this command, there should be some lines like (the output on my pc):
```
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

This means that in my case **LVDS1** is connected and the commands will be passed to it. For you if you have different one then replace "**LVDS1**" in my code with what is connected in your output.

2- in Terminal:
```
cd ~/Desktop
gedit rotate_left.desktop
```

3- when the text editor opens up paste the following code in it (note: don't forget to replace my **LVDS1** with that is connected in your output):
```
[Desktop Entry]
Type=Application
Terminal=false
Name=rotate_left
Exec=xrandr --output **LVDS1** --rotate left
Name[en_US]=rotate_left
```

4- save and close.
5- in Terminal:
 ```
sudo chmod 755 rotate_Left.desktop
```

Now you got an executable file on your desktop to rotate the whole screen 90 degree to the left.
to create the other rotations files you do the same steps replacing the word "left" with "right", "inverted" or "normal".

Hope that helped you for the mean time :)

---

### Post by winslowevan2 on 2013-12-15
Thanks! Thats exactly what I needed!

---

### Post by mörgæs on 2013-12-15
Good, but are you aware that 10.04 is unsupported (meaning that security bugs are not corrected)?

---

### Post by asus-user on 2013-12-15
> **mörgæs said:**
> Good, but are you aware that 10.04 is unsupported (meaning that security bugs are not corrected)?

aw, you might be right, I tested my code only on Ubuntu 12.04.

---

### Post by mörgæs on 2013-12-16
I meant that original poster should install a supported version and try your code in that :-)

---

### Post by asus-user on 2013-12-16
> **winslowevan2 said:**
> I have a tablet PC I bought for reading PDFs and it has no keyboard so I can't bind keys easily. I want to create a desktop icon so that I can rotate 90 degrees each press. Thanks!

Here it is with one single executable file on desktop:
1- in Terminal:
```
gedit rotationCode.sh
```
in the opened text editor paste the following code:
```
#!/bin/bash
current_rotation=`xrandr -q --verbose|grep LVDS1|cut -d ' ' -f5`
if [ $current_rotation = "normal" ]
then
    xrandr --output LVDS1 --rotate left
elif [ $current_rotation = "left" ]
    then
    xrandr --output LVDS1 --rotate inverted
elif [ $current_rotation = "inverted" ]
    then
    xrandr --output LVDS1 --rotate right
else
    xrandr --output LVDS1 --rotate normal
fi
```
save and close.
2- in Terminal:

```
sudo chmod 755 rotationCode.sh
```

3- In Terminal use the command:
```
xrandr
```
to see the connected screen (LVDS1, HDMI1, VGA1, ..) I will consider here that **LVDS1** is connected.
4- in Terminal:
```
cd ~/Desktop
gedit rotate.desktop
``` 
 when the text editor opens up paste the following code in it (note: don't forget to replace my **LVDS1** with that is connected in your output):
```

[Desktop Entry]
Type=Application
Terminal=false
Icon=rotate
Name=rotate
Exec=./rotationCode.sh
Name[en_US]=rotate 

```
 save and close.
5- in Terminal:
 ```
sudo chmod 755 rotate.desktop
```

close Terminal and that's it.

Now you have a single executable file on your desktop to make a 90 degree rotation every time it is executed :)

---

### Post by winslowevan2 on 2013-12-16
I am upgrading currently, and I did not know, thanks!

---

### Post by asus-user on 2013-12-16
You're welcome.
If you have no more questions related to this topic, please mark this thread as [SOLVED].

---

