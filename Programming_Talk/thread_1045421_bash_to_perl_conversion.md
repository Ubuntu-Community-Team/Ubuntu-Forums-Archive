---
title: "bash to perl conversion"
date: 2009-01-20
forum: Programming Talk
---

### Post by Aoko on 2009-01-20
```
	PROC=$(ps -u `whoami` | grep -v grep)
	if [[ `echo $PROC | grep mplayer` ]]; then
		VP=$(ps -u `whoami` | grep -vE "grep|[^\/]smplayer" | grep mplayer)
		FNAME=$(basename "$(readlink /proc/$(echo $VP | sed 's,\([0-9]\)\s.*$,\1,g')/fd/3)")
```

Can someone help me with converting the above bash to perl please

---

### Post by slavik on 2009-01-20
Where did you get this and what exactly is it doing?

I am currently deciphering this. :)

EDIT:
OK, I am wondering who wrote this as this is very convoluted and not very nice.
Still wondering why you need this in Perl ... here's a simpler command to run:
```

ps www -u `whoami` | grep -v grep | grep `which mplayer` | tr -s ' ' | sed 's/.*\///g'

```

EDIT2:
For those who can't figure it out. the code simply looks up the file which mplayer has opened first (the assumption is made that it opens the actual media file for playing before opening any pipes/sockets/other files.)

What I have provided is something that I feel will work better, since it looks at the last argument to mplayer, which has to be a file. :)

---

