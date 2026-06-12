---
title: "Zenity notification icon"
date: 2007-02-09
forum: Programming Talk
---

### Post by Balaam's Miracle on 2007-02-09
Here's a little script i've made to keep track of my uptime. It basically works as i want it to (left out the comments):
```

#!/bin/bash
function uptim {
export UPT=`uptime`
    zenity --text "Uptime is $UPT" --notification
uptim
}
uptim
```

However, this does put an ugly orange warning icon on the panel, but i would want to use my own. Does anybody know if this is possible with Zenity?

---

### Post by Tomosaur on 2007-02-09
Yup, like this:
```

zenity  --notification  --window-icon=/path/to/my/picture.png  --text "Hello"

```

---

### Post by Balaam's Miracle on 2007-02-09
> **Tomosaur said:**
> Yup, like this:
```

zenity  --notification  --window-icon=/path/to/my/picture.png  --text "Hello"

```

Thanks a bunch for the help! For some reason this option did not make it to the docs, at least not the docs that i have found.

---

### Post by Tomosaur on 2007-02-09
It's mentioned near the bottom of the man page, but yeah, it is obscure :S

---

### Post by kkharinarayanan on 2011-01-05
hi guys i just did a script to use zenity  to show icon in notification area and osd to display messages every one hour. hope any body will find it useful

 
ps -ef | grep -v grep | grep "zenit"                   # to check if zenity is running ie if the proram is runnin already if it is runnin then the following parts are  
                                                       # executed . so that even if you log out the notification area icons dosent croud about
if [ $? -ne 0 ]; then

 ~/Uptimechild.sh                                      # call the script that displays notification area icon
  while true; 
    do
    sleep 3600                                         # wait till 1 hour is elapsed
    notify-send "Up Timer"  "You have been logged in now for "$y" hours."  # shows osd each hour
    y=$(($y+1))
  done

fi
 
just replace  ~/Uptimechild.sh  with the path to the original script

---

### Post by kkharinarayanan on 2011-01-05
hi guys i just did a script to use zenity  to show icon in notification area and osd to display messages every one hour. hope any body will find it useful

 
ps -ef | grep -v grep | grep "zenit"                  
# to check  if zenity is running ie if the proram is runnin #already if it is runnin then the following parts are  
# executed . so that even if you log out the notification area #icons dosent croud about

if [ $? -ne 0 ]; then

 ~/Uptimechild.sh                                     
# call the script that displays notification area icon
  while true; 
    do
    sleep 3600                                        
# wait till 1 hour is elapsed
    notify-send "Up Timer"  "You have been logged in now for "$y" hours." 
# shows osd each hour
    y=$(($y+1))
  done

fi
 
just replace  ~/Uptimechild.sh  with the path to the original script

---

