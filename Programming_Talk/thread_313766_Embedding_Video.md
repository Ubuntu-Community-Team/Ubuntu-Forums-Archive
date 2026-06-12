---
title: "Embedding Video"
date: 2006-12-06
forum: Programming Talk
---

### Post by lovloss on 2006-12-06
This is an extremely complicated question. I hope someone can help me.

 I have a web site : [http://www.vasilisagames.com](http://www.vasilisagames.com)   Its supposed to have an intro video. On linux, of course, the mplayer plugins run it no problem, but on any other computer i go on it gives either a quicktime error message or a windows media player message. My site is anti-microsoft open source, so i cant have that.
 
 I want to know how to embed this video into my site in such a way that it can be easily accessed without making too many people get complicated plug-ins. I need to know what type of video to convert this to, if anyone knows how to effectively embed it, and finally, how on earth to transcode it. I hate mencoder and ffmpeg, they're so complicated >.< And i cant find a single GUI that works for it.

 can anyone help me out?

---

### Post by hod139 on 2006-12-06
I'm running linux, and I can't view the video.  I get the error message:
Totem could not play 'fd://0'.
What kind of move is it? It sounds like you don't want it, but I have a mencoder command laying around somewhere for creating divx files that are compatible across platforms if you want it.

---

### Post by lovloss on 2006-12-06
Please! I would like that way mucho!

---

### Post by hod139 on 2006-12-06
I'm not exactly sure how you are making the movie, but this command converts an avi into a divx file.
```

mencoder input.avi  -ovc lavc -ffourcc DX50 -lavcopts vcodec=mpeg4:mbd=2:trell:v4mv:turbo -o output.avi

```

The important option is 
-ffourcc DX50
which allows Windows to recognize the movie and play it (after downloading the divx plugin that is).

---

### Post by lovloss on 2006-12-06
Thank you SO much!!!

---

