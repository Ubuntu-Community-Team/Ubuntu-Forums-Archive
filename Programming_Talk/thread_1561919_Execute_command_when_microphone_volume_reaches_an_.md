---
title: "Execute command when microphone volume reaches an arbitrary level"
date: 2010-08-26
forum: Programming Talk
---

### Post by robjoski on 2010-08-26
I am trying to write a shell script to make my computer beep when I shout into the microphone too loud. For retrieving the volume level, I found [http://ubuntuforums.org/showpost.php?p=6505818&postcount=6](http://ubuntuforums.org/showpost.php?p=6505818&postcount=6), which is written in Python - but I can't seem to figure out how to convert its output to something useful. I also started a Python version of my script, but I gave up because executing one simple command is so darn tedious... Here's what I have so far:
```

#!/bin/bash
MICVOL=`./getvolume.py`
MINV=1000
MAXV=30000
while true; do
if [ $MICVOL -gt $MINV ]; then
beep -f 600 #or some other command
elif [ $MICVOL -gt $MAXV ]; then
echo "Stop cursing!" && beep -f 500 -r 10 -l 100 -D 10
fi
done

```I had to slightly modify getvolume.py so it would only output one value and exit, otherwise it would be kind of like interactively executing "yes"... For some reason MICVOL isn't updated every time I access it, and if it's not at the MINV threshold when I start the script, it never beeps. Any pointers?

---

