---
title: "[SOLVED] Video with a creative Zen in Ubuntu"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by natman on 2008-05-28
I have a Creative Zen, and it plays video. The program that compresses the video res. down for the player will work in windows. Is there an equivalent version in linux?
I have a video file 624x352 350mb 23fps xvid and my zen plays files like
320x176 23fps xvid.
I have wine but have no idea which program on the cd rom does the conversion.

---

### Post by quelx on 2008-05-28
[http://www.anythingbutipod.com/forum/showpost.php?p=220283&postcount=4](http://www.anythingbutipod.com/forum/showpost.php?p=220283&postcount=4)

---

### Post by natman on 2008-05-28
That link didn't really help can someone jst show me a script or a line of code that will do what i need ( i could not understand the line of code in the above link )

---

### Post by quelx on 2008-05-28
open a terminal window (**ALT-F2** > **gnome-terminal**)
```
sudo apt-get install mencoder mplayer
```

paste this into the terminal change the **in.avi** and **out.avi** to your original avi file and what you want to call the new one encoded for the Zen.

```
mencoder in.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=512:vhq:keyint=250:threads=2 -oac mp3lame -lameopts cbr:br=64 -ffourcc XVID -vf scale=320:-2,crop=320:240,expand=320:240 -af resample=44100:0:0 -o out.avi
```

---

