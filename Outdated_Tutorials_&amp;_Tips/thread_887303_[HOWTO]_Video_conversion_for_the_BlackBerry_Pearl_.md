---
title: "[HOWTO] Video conversion for the BlackBerry Pearl 8100"
date: 2008-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by QwUo173Hy on 2008-08-12
The BlackBerry Pearl 8100 is quite fussy about what it will play. This is the only way I have been able to convert my videos to play on this device. 

```
 mencoder -vf scale=240:-10 <input file> -o <output file> -of avi -ofps 15 -ovc lavc -oac mp3lame -lavcopts vcodec=mpeg4:vbitrate=230:acodec=mp3:abitrate=64

```

Note, make sure your output file has the .mp4 extension.

---

### Post by tcpankon on 2008-09-03
Posted this elsewhere, but it is applicable here.  

I still need to add some error checking and perhaps user input for sub-directory naming; but for now, copy this script to a directory containing .avi's you wish to convert and simply run it. It will grab all avi's and convert to .mp4 files capable of being viewed on a blackberry (tested on 8130 pearl). A pearl folder will be created and all the mp4 files will be in this directory. Seems to take about 10 minutes for a 170 Mbit avi. Once done, the file size should be a little less than half of what it was.

```
#!/bin/bash
VAR="files.txt"
ls *.avi | sort > $VAR
mkdir pearl
cat $VAR | while read line; do
  INPUT=$(echo ${line})
  OUTPUT="pearl/"
  OUTPUT+=${INPUT%.avi}
  OUTPUT+=".mp4"
  mencoder "$INPUT" -oac lavc -ovc lavc -of lavf -lavcopts  global=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=240:180,harddup -ofps 30000/1001 -o "$OUTPUT"
done
rm $VAR
```

Please post any suggestions to maintain quality yet decrease size, or anything else that may be sueful

---

### Post by PerfectReign on 2009-09-27
@Jarlath - you rock!

I got my file to convert without a hitch. Now just to put it in a script.

---

### Post by PerfectReign on 2009-09-27
Okay, take it back.  It converts, but the sound is off by about four seconds.  

Any ideas how to coordinate?

---

### Post by QwUo173Hy on 2009-09-28
There's a -delay option in the man-pages. I'd imagine it's something like '-delay +4' (or -4)

---

