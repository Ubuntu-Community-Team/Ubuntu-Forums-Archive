---
title: "[SOLVED] background changer"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Ketson on 2008-04-25
does any one know of any apps that can be used to change the background periodically. I have tried 'chbg' but I seem to be having a few issues with that working. any suggestions on what else can be used would be much appreciated.

---

### Post by mister_pink on 2008-04-25
You can make a script yourself fairly easily to do this. This is a fairly basic one that simply takes a random .jpg from a folder and sets it as the background. Make it executable and set it as a cron job (run crontab -e to set it up, look cron up on wikipedia for the syntax)
```

#!/bin/bash
DIR="/path/to/your/wallpapers/"
NIMGS=`find $DIR -iname '*.jpg' | tr -d ' '` 
IMGS=`find $DIR -iname '*.jpg' -printf "%p#"`
N=`echo $NIMGS | wc -w`
if [ $N -eq 0 ]; then
  echo "No jpeg images found - extension must be .jpg"
  exit 1
fi
RANDOM=$(head -1 /dev/urandom | od -N 1 | awk '{ print $2 }')
M=$(( ($RANDOM%$N+1) ))
BGNAME=`echo $IMGS | cut -d '#' -f $M`
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$BGNAME" 
exit 0

```

Edit: I should mention, any paths or filenames with a space in will break this...

---

### Post by zach382 on 2008-04-25
Look for Desktop Drapes in the repository.
```
sudo apt-get install drapes
```

---

### Post by Schendje on 2008-04-25
> **zach382 said:**
> Look for Desktop Drapes in the repository.
```
sudo apt-get install drapes
```

Yeah, try Desktop Drapes. It's easy to use and it works great. 

Only thing bothering me is that it's always showing in the taskbar... Is there a way to get change this?

---

### Post by Ketson on 2008-04-25
Used Drapes just what I was looking for.

Thanks

---

