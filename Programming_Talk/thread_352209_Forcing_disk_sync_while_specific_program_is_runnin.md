---
title: "Forcing disk sync while specific program is running"
date: 2007-02-03
forum: Programming Talk
---

### Post by gmc on 2007-02-03
Hi Folks,  I´m stuck on a little problem that I can´t quite wrap my brain around.           

```

#!/bin/bash

OUTPUT="/home/gord/Desktop/pvr/`date +%y%m%d-%H%M.avi`"

mencoder /dev/video1 \
         -ovc lavc    -lavcopts vcodec=mpeg4:vbitrate=1400:keyint=30 \
         -oac mp3lame -lameopts cbr:br=128:mode=3 -vop scale=528:360,pp=lb \
         -endpos 00:29:59 -o $OUTPUT

exit 0

```In the above script, I´m using mencoder to record a video stream from /dev/video1 for 29:59. What I´d like to do is force a disk ´sync´ every 5 seconds during the time that mencoder is running and then stop.  Does anyone have any idea´s how this could be accomplished?  

Gord

---

### Post by lnostdal on 2007-02-03
maybe: man 1 sync

---

### Post by gmc on 2007-02-03
> **lnostdal said:**
> maybe: man 1 sync

Thanks Inostdal,

I should have tried IRC before posting. I´ve got my solution... here it is:

```
#!/bin/bash

OUTPUT="/home/gord/Desktop/pvr/`date +%y%m%d-%H%M.avi`"

mencoder /dev/video1 \
         -ovc lavc    -lavcopts vcodec=mpeg4:vbitrate=1400:keyint=30 \
         -oac mp3lame -lameopts cbr:br=128:mode=3 -vop scale=528:360,pp=lb \
         -endpos 00:29:59 -o $OUTPUT **&**

[B]while [ ¨$(pidof mencoder)¨ != ¨¨ ]; do sync; sleep 5; done
[/B]
exit 0
```This executed mencoder in the background and then enters a loop that executes ´sync´ every 5 seconds until mencoder stops.

Thanks
Gord

---

