---
title: "yahoo mail notifications on notification area"
date: 2009-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by ~Las~ on 2009-10-26
Since current repo mail notification system dosent support yahoo tried to fill the gap.
Got fetchyahoo perl script current ver.from [http://fetchyahoo.twizzler.org/](http://fetchyahoo.twizzler.org/) and edited as it needs and replaced original one. It is easily configurable because of comments it provides.And wrote a notification icon from zenity.Since coads are big I only post notification code & modified fetchyahoo is attached.I dont know how to give relative paths so all i edited are not realative paths.they are in between 1218 &1249 lines in modified fetchyahoo file.Im new to programming still learning thru google:)

notification code 

```
#!/bin/bash

textArray[0]="" # hold text
c=0 # counter
# read whole file in loop
while read LINE
do

  textArray[$c]=$LINE # store line
  c=$(expr $c + 1) # increase counter by 1
done < /tmp/data.txt




 
# This will start zenity, and its stdin is linked to file descriptor 3
exec 3> >(zenity --notification --listen --window-icon=/usr/share/icons/hicolor/48x48/apps/mail-notification.png)
echo "tooltip:${textArray
[*]}" >&3 

sleep 120


# close the file descriptor. This will also kill zenity.



exec 3>&-  

```

Hope someone find it useful in the same manner I does

---

