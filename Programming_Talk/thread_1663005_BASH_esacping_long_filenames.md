---
title: "BASH esacping long filenames"
date: 2011-01-09
forum: Programming Talk
---

### Post by martinjh99 on 2011-01-09
Given this BASH script to dump the audio from FLV files as mp3s it doesnt work on files with spaces in...

How do I get it to handle space in filenames?

```

#!/bin/bash

OUTPUTDIR="mp3/"

for FILE in *flv; do

ffmpeg -i $FILE -acodec libmp3lame -ab 256k -ac 2 -ar 44100 $OUTPUTDIR$FILE.mp3

done

```

---

### Post by andrew.46 on 2011-01-09
Perhaps the following small variations might help:

```

#!/bin/bash

OUTPUTDIR="mp3"

for FILE in *.flv; do

ffmpeg -i "$FILE" -acodec libmp3lame -ab 256k -ac 2 -ar 44100 $OUTPUTDIR/"${FILE%.flv}.mp3"

done

```

Andrew

---

### Post by martinjh99 on 2011-01-09
Bingo - Thanks mate!

---

