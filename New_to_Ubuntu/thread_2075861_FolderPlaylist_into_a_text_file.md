---
title: "Folder/Playlist into a text file"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Nikola Georgiev on 2012-10-24
I want to make te list of files in a folder with video and audio files to a text file with the songs/videos and their enduring.
For example:

01. track 01 - songname.mp3 - 04:35min
02. video 01 - videoname.flv - 05:01min
etc...

Is there an easy way to do this, because I just want to print the list.

---

### Post by Nikola Georgiev on 2012-10-25
Up?

---

### Post by Vaphell on 2012-10-25
```
for f in *.{mp3,flv,avi}; do printf "%s\t%s\n" "$f" $( ffmpeg -i "$f" 2>&1 | awk '/Duration/{ sub(/,/,"",$2); print $2; }' ); done > list.txt
```

---

