---
title: "Webcam Background Change"
date: 2008-09-23
forum: Programming Talk
---

### Post by Blacklemon67 on 2008-09-23
I've developed a script that downloads a file then sets it as the desktop background. 

```

#!/bin/sh

cd /home/david/Pictures/
rm "webcam3_large30.jpg?1199825159537"
wget --no-proxy -q -N "http://www.portstcharles.com/~webcams/webcam3_large30.jpg?1199825159537"
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/home/david/Pictures/webcam3_large30.jpg?1199825159537"

```

The code works, but there are a few bugs,
[LIST=1]
[*]Sometimes the download doesn't run smoothly and I end up with a big black bar near the bottom or the whole image.
[*]The program accidentally downloads the same file twice even though I have timestamping enabled
[*]And I can't find a way to put it in a loop or stop it when I want, It's currently just a button that you need to click to refresh.
[/LIST]

Any suggestions are welcome =P

---

### Post by Blacklemon67 on 2008-09-23
Bump :confused:

---

