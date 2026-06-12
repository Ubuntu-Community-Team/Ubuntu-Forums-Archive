---
title: "Bash script help"
date: 2011-10-16
forum: Programming Talk
---

### Post by bilbs84 on 2011-10-16
First of all, not sure if this is in the right place, but here go's anyway

Hi, im a total noob to Linux, been using ubuntu with KDE for about a week now, and so far am happy and learning my way round.
I decided to try and write a script for Youtube vids, it can pull the vid title using wmctrl and grep, then i can get url with grep from mozilla's sessionstore.js, unless there are unusual characters in the page title
This is the code in my script, and it works for vids with a fairly normal title

dlyt
```

#!/bin/bash
wmctrl -l > te1.t
te1=$(grep Nightly te1.t)
te2=${te1##*USB3 }
tit='"'${te2%* - Nightly}'"'
title=${te2%* - Nightly}
u=$(grep -oP '"url":"\K[^"]+","title":'"$tit"'' $(ls -t ~/.mozilla/firefox/*/sessionstore.js | sed q))
url=${u%*'","title":'$tit}
echo Downloading from
echo $url
./youtube-dl -o "$title.mp4" $url
rm te1.t

```To use this, i load the YouTube page in firefox, then from bash i run 
```
./dlyt
```So if youtube vid is "Example Song - YouTube", everything works sweet, wind up with a video names Example Song - Youtube.mp4 in dir i run file from
But if video title was "Example Song (Artist) - YouTube" then grep wont dump the url to u, im assuming its the () doing this, a . in the title also causes problems, as well as #$!, anything unusual gives me no luck, ive been at this for a day now, and any help would be appreciated.

---

### Post by bilbs84 on 2011-10-22
Solved this, using title=${tit%%(*} to remove the ( from the title, now all is good, if anyone wants the complete code let me know, makes life so easy

---

### Post by mörgæs on 2011-10-22
Renamed, moved to Programming Talk and marked Solved.

---

