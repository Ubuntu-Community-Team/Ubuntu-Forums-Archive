---
title: "lftp bash script"
date: 2010-11-12
forum: Programming Talk
---

### Post by jaypah89 on 2010-11-12
i want to make a little bash script for my downloading need. i'm using lftp and want to use zenity as interface. but i'm having a problem as i dun really understand the lftp command. my script:

```
#!/bin/sh

url=`zenity --title="Lftp " --text="Enter url" --entry`

lftp -e 'pget -n 40 "$url"; quit'

notify-send -u normal -t 2000 -i gtk-ok "Lftp" "Download of $url complete"
```

if possible i wanna add zenity interface to show the progress of download but i don't know how. any advice would be much appreciated.

---

### Post by jaypah89 on 2010-11-12
i've made a few adjustment on the script. now it can be use with flashgot (add-on for firefox). but it is still lack of a proper progress bar. for now i make the progress to be shown in the terminal. don't forget to give permission to the script.

```
#!/bin/bash

# lftp-flashgot.sh

URL="$@"
SAVE=$(zenity --title="Lftp: Save to:" --file-selection --filename="$URL" --save --confirm-overwrite) ;echo $SAVE

cd "$(dirname $SAVE)"
gnome-terminal --geometry=125x5 -x lftp -c "pget -n 40 $URL;quit" || asplode

notify-send -u normal -t 2000 -i gtk-ok "Lftp" "Download of $URL complete"  
```

how to use with firefox?
install flashgot add on- go to tools- flashgot- more options- click add- put any name u like (i use Lftp)- in executable path locate the bash script (~/Desktop/lftp-flashgot.sh or anywhere u save it- click OK button.

enjoy your blazing fast download..

---

