---
title: "Problems passing parameters to rsync in script"
date: 2009-10-29
forum: Programming Talk
---

### Post by keta on 2009-10-29
First of all, I must say that I'm a newbie in scripting. That being said, I need some light on what's happening here; consider the following script (NOTE the -n "dry run" option, the script will do really nothing):

```
#!/bin/bash

BROOT="/home/keta"
BDIR="/backup try"
BFULL=\'$BROOT$BDIR\'

echo ; echo "BFULL = $BFULL" ; echo # Just to show it's right

rsync -av --delete -n $BFULL /tmp
```I want to tell rsync that the source directory is '/home/keta/backup try' (with the quotes because of the blank space) (the reason BFULL is split in two is because this is part of a bigger script... not a big deal I guess). Instead, rsync thinks that the source directory is in /wherever/you/are/'/home/keta, and the source is /wherever/you/are/try. I tried several forms, and weird things happen always. Why is this, and how can I do to pass what I want to rsync?

---

### Post by ViRMiN on 2009-10-29
[Ignore]

---

### Post by ViRMiN on 2009-10-29
Actually, the more I think about what I've suggested, the less faith I have!

```

#!/bin/bash
BROOT="/home/keta"[FONT=monospace]
[/FONT]BDIR="/backup try"
BFULL=$BROOT$BDIR

echo ; echo "BFULL = $BFULL" ; echo # Just to show it's right

rsync -avs --delete -n "$BFULL" /tmp

```This one might work better

---

### Post by keta on 2009-10-29
Thanks a lot, your second suggestion did it! Man, I thought I had tried that one myself, looks like I didn't hehehe ;)

Thanks again! :D

---

### Post by ViRMiN on 2009-10-29
> **keta said:**
> Thanks a lot, your second suggestion did it! Man, I thought I had tried that one myself, looks like I didn't hehehe ;)

Thanks again! :D

No problem, gave me something to think about for a few minutes!  I don't know why the quotes have to be around $BFULL in the rsync string but, they do.  Tried different ways and all fail unless I double-quote the variable like that.

Someone else might come up with another way of doing it?  Or even explain the need for that double-quoting?

---

### Post by ViRMiN on 2009-10-29
Did you put the '-s' switch on rsync when you re-tried, or did you copy & paste all my text?

I had a quite squint at the man page and it said it was necessary for paths containing whitespace...

---

### Post by keta on 2009-10-29
I just copied the text and it worked. Did an actual try and it worked without problems. I don't really know if the -s option would be of any help here.

Cheers,

Keta

---

