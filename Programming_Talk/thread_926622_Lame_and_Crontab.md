---
title: "Lame and Crontab"
date: 2008-09-22
forum: Programming Talk
---

### Post by LeoKent on 2008-09-22
I am creating script to automatically download audio streams and then converts them into an MP3. However I am having problems with LAME when it is run from a crontab.

Below is a (very) simplified version of my script. I have made it executable by running "chmod u+x convert.sh".

```

#!/bin/bash
lame /home/leo/audio.wav /home/leo/audio.mp3

```

This runs fine if I start it manually with "sudo ./convert.sh". [Please note I am running as root because I am also modifying files in /var/www.]

However if I run this as a crontab, example below, the MP3 file created has only the first 5 seconds of the audio.

```

0 12 * * * /home/leo/convert.sh

```

I do not understand why this works when run from console but not when run as a crontab. Can anyone hep?

---

### Post by Zugzwang on 2008-09-22
Try passing the terminal output of lame to some file in order to get error messages that may occur:
```

#!/bin/bash
lame /home/leo/audio.wav /home/leo/audio.mp3 > /home/leo/lame_log.txt

```

---

### Post by ianhaycox on 2008-09-22
It might be because the shell script is generating output and this output is then emailed to root by cron. That bit might be broken.

Try adding 2>&1 >> /tmp/lamelog to your crontab entry or using options for lame to make it quiet, and try again.

---

### Post by LeoKent on 2008-09-22
> **ianhaycox said:**
> It might be because the shell script is generating output and this output is then emailed to root by cron. That bit might be broken.

Try adding 2>&1 >> /tmp/lamelog to your crontab entry or using options for lame to make it quiet, and try again.

Still not working. What's more, nothing has been outputted to /tmp/lamelog. Haven't tried quiet yet.

EDIT: Fixed - Added "-S" to lame. Thanks.

---

