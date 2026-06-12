---
title: "xrandr and Nvidia"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by nitsuJredynS on 2014-03-04
hi having trouble, got icon to appear but does not respond, please help me correct this... 

xrandr = 

Screen 0: minimum 832 x 525, current 2880 x 900, maximum 2880 x 900
default connected 2880x900+0+0 0mm x 0mm
   2880x900       50.0* 
   2464x900       51.0  
   960x600        52.0  
   960x540        53.0  
   840x525        54.0  
   832x624        55.0  

so i made my rotationCode.sh look like this :

#!/bin/bash
current_rotation=`xrandr -q --verbose|grep default|cut -d ' ' -f5`
if [ $current_rotation = "normal" ]
then
    xrandr --output default --rotate left
elif [ $current_rotation = "left" ]
    then
    xrandr --output default --rotate inverted
elif [ $current_rotation = "inverted" ]
    then
    xrandr --output default --rotate right
else
    xrandr --output default --rotate normal
fi

i am thinking since i am using an NVIDIA interface with dual screens the xrandr isnt recognizing the correct path

---

### Post by oldos2er on 2014-03-04
Post moved to its own thread.

You might want to specify which version of Ubuntu you're using.

---

