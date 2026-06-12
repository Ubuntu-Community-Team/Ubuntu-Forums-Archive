---
title: "Show Progress with Nautilus script"
date: 2009-08-25
forum: Programming Talk
---

### Post by handband2 on 2009-08-25
I have a script which I run to convert my .MTS videos to .flv.  The script is in my Nautilus script folder.  When I run the script it runs perfectly fine in the background without showing me any progress.  I would like to see the progress of the conversions.

I've tried to get gnome-terminal and xterm pop-up to show the progress without success.  I would appreciate it if someone could help, thanks!

```

#!/bin/bash

mkdir ./converted

for f in *.MTS; do ffmpeg -i "$f" -vcodec libx264 -acodec libmp3lame -ar 22050 -ab 32K -s 768x432 -f flv ./converted/"${f%.mpg}.flv"; done

```

---

### Post by Copernicus1234 on 2009-08-25
This may be a bit of work, but you could build a small gtk program that only has a button and a progressbar. When clicking the button, your script starts to run. Every second it asks the script for progress and updates the bar. 

Im not aware of any easy way to show a graphical progress bar Im afraid, but then again I havent scripted for Nautilus. Perhaps there is a way.

---

### Post by johnl on 2009-08-25
Hi,

You can use 'zenity' with the '--progress' option to show a progress bar.  I have never used it myself so I can't give you much more info, but someone else here or google might be able to :)

---

### Post by handband2 on 2009-08-26
> **johnl said:**
> Hi,

You can use 'zenity' with the '--progress' option to show a progress bar.  I have never used it myself so I can't give you much more info, but someone else here or google might be able to :)

Thanks!  I got it fixed with zenity.  This is what I ended up with:
```

#!/bin/bash

# Dialog box
SIZE=`zenity --list --title="Choose Resolution" --radiolist --column="Check" --column="Size" "" "480×272" "" "512x288" "" "768x432" "" "1024x576" "" "1280x720"`

if [ "${SIZE}" == "" ]; then    
zenity --error --text="Size not defined by user.
Please choose a size to use. "
exit 1
fi

# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find . -maxdepth 1 -type f -name "*.MTS" | wc -l`
let "INCREMENT=100/$NUMBER_OF_FILES"

mkdir ./converted

# Converting Files
(for f in *.MTS; do
echo "$PROGRESS";
echo "# Converting $f";
ffmpeg -i "$f" -vcodec libx264 -acodec libmp3lame -ar 22050 -ab 32K -s "${SIZE}" -f flv ./converted/"${f%.mpg}.flv"
let "PROGRESS+=$INCREMENT"
done
) | zenity  --progress --title "Converting Files..." --percentage=0

```

---

