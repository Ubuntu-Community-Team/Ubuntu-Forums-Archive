---
title: "help with AVI to DVD ISO script"
date: 2006-10-14
forum: Programming Talk
---

### Post by lucia_engel on 2006-10-14
Hi, I wrote a script to convert AVI files to a DVD ISO file using the HOWTO guide [http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux"): 

```

#!/bin/bash

# Written by: Alice Leung
# Thanks to jtpratt who wrote the "Converting video in linux using
# ffmpeg and memcoder" guide which you can find here:
# http://smorgasbord.net/convert_video_linux



# Converts AVI videos to an DVD ISO file
# Requires ffmpeg, dvdauthor, and mkisofs



mkdir ./iso
for i in *.avi; do ffmpeg -i "$i" -target ntsc-dvd ./iso/mov$((++c)).mpg; done
cd ./iso
dvdauthor -o . *.mpg
dvdauthor -o . -T
rm -f *.mpg
mkisofs -dvd-video -o ./movie.iso .

```

I've tested the script and it works, but if there is insufficient space, the script would continue to run, thus making an empty iso. Is there a way I can catch the error of not enough hard drive space, and then after the user increase it, a restart of the script would resume where it stopped?


And can anyone recommend a website or two that has samples of script source code I can look at to learn more about scripting. Thanks

---

### Post by Drakx on 2006-10-14
try having the script do ls -lh to see how much disk space is free

Edit:

Sorry i meant df and if it's less then say 4.5gig stop the script and tell the user not enough space

---

