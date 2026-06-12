---
title: "[SOLVED] troubble with AT and DISPLAY for vlc."
date: 2008-08-20
forum: New to Ubuntu
---

### Post by schmick on 2008-08-20
Hi there!
First I had trouble with _*at*_ because it wanted to send a confirmation mail. So I had to install sendmail (any other option beside it?)
OK, no more errors, but trying to do a;
at now + 5 minutes
at> vlc --volume 500  /home/blablabla/Music/moreblablabla.mp3
.....

So, I received a nice mail (had to install mailx to read it though)
---
VLC media player 0.8.6e Janus
Error: Unable to initialize gtk, is DISPLAY set properly?
---

I guess there are other cli players, but.. if I realy REALY want to get some gnome prog running... what can be done for the display?
btw, what cli player is available?... I want an alarm clock. :)
ThX!

---

### Post by pauper on 2008-08-20
```
:~$ echo $DISPLAY
[highlight]:0.0[/highlight]
:~$ at now + 1 minute
warning: commands will be executed using /bin/sh
at> export DISPLAY=[highlight]:0.0[/highlight] && vlc /path/to/file
at> <EOT>
job 01 at Wed Aug 20 11:30:00 2008
:~$ 
```

[edit:]

[http://tux.50webs.org/review_cli_audio_tools.html](http://tux.50webs.org/review_cli_audio_tools.html)

---

### Post by schmick on 2008-08-21
That's what I call an answer!
Thx Pauper!

---

