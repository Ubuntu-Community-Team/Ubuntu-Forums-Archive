---
title: "Basic bash help"
date: 2007-11-08
forum: Programming Talk
---

### Post by ridetheteapot on 2007-11-08
```
#!/bin/bash

npr1=du -k "/home/ortango/playlists and webcasts/"*`date +%b%d`* | cut -f 1
sleep 20
npr2=du -k "/home/ortango/playlists and webcasts/"*`date +%b%d`* | cut -f 1
if $npr1 = $npr2
then
  "/home/ortango/bin/stopnpr.sh"
  mv "/home/ortango/playlists and webcasts/"*`date +%b%d`* "/home/ortango/playlists and webcasts/failed/wyncmorn_"`date +%b%d%l:%M`.mp3
  "/home/ortango/bin/recordnpr.sh"
fi

```
thats what i have, but my npr1 assignments are not working.
i tried npr1=${.....}
but that didn't work for me either and i trie `backticks` around the statement

the code is for restarting a mplayer streamdump that had lost its connection (mplayer keeps running in this case, so checking the pid doesnt work). cron will run this script every few minutes while the recordnpr.sh is schedueled.

---

### Post by geirha on 2007-11-08
either use $( ... ) or ` ... \`date +%b%d\`* ... `

---

### Post by ridetheteapot on 2007-11-08
used the first one.

i gotta say bash syntax is tough, its not like c.

im still havein problems with my if statements(oh the regression), but i'm pretty sure i've got it down now. thanks for the hand

---

