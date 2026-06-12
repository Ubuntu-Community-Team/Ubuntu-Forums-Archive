---
title: "XWinWrap Movie Background"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by blendmaster on 2008-11-09
Hello!

So I'm using XWinWrap to try and play movies on my desktop's background. I got screensavers to play, so I know it's working. However, I try to play a movie with the following command:

```
xwinwrap -ni -o 0.8 -fs -s -st -sp -b -nf -- vlcplayer -wid WID -loop 0 ~/movie.mpg

```

and it tells me the following result:

> mplayer: No such file or directory
mplayer died, exit status 2


The movie is in that location, with that exact name. I opened mplayer to try to open the file location (ctrl-l), but it gives me a location not found error too.

Any ideas?

---

### Post by blendmaster on 2008-11-09
Anyone got any ideas?

---

### Post by Bölvaður on 2008-11-09
check the file for rights, user and try change name and location, even just try a different file.

and also -- vlcplayer is strange when you are going to be trying mplayer, perhaps write mplayer instead?


These are just simple suggestions.. I have no idea, but my attentions are good so that counts :KS

---

### Post by blendmaster on 2008-11-09
> **Bölvaður said:**
> check the file for rights, user and try change name and location, even just try a different file.

and also -- vlcplayer is strange when you are going to be trying mplayer, perhaps write mplayer instead?


These are just simple suggestions.. I have no idea, but my attentions are good so that counts :KS

Oops, I've tried both mplayer and vlcplayer (I accidentally quoted with vlcplayer).

I've tried a .mkv and a .mpg, I've renamed one file from its original name to movie.mpg. It's readable by mplayer through opening the file from it's directory path (or just double-clicking). It seems to me to be some sort of problem with mplayer/vlcplayer.

I have no idea either, lol, Thanks for the suggestions!

---

