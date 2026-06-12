---
title: "bash: how to dump a stream with mplayer and stop it after 30min"
date: 2009-09-14
forum: Programming Talk
---

### Post by frenchn00b on 2009-09-14
Hello

I run :
```
#!/bin/sh

mplayer -dumpfile $HOME/dumpmp3.mp3 -dumpstream "http://players.creacast.com/creacast/france_info/playlist.m3u"

```

and would like it to stop dumping after 30min

How can I make it ? I would like to implement this recording into the script, and not tweaking with crontab killing.

It runs from the crontab, so no X.

---

### Post by Yannick Le Saint kyncani on 2009-09-14
```
#!/bin/sh

mplayer -dumpfile $HOME/dumpmp3.mp3 -dumpstream "http://players.creacast.com/creacast/france_info/playlist.m3u" &
sleep 1800
for s in HUP INT KILL; do
    kill -$s $! &>/dev/null || break
    sleep 5
done

```

---

### Post by andrew.46 on 2009-09-14
Hi frenchn00b,

Another variation:

```

#!/bin/sh

mplayer -cache 2048 -min-cache 80 \
        'http://players.creacast.com/creacast/france_info/playlist.m3u' \
        -dumpstream -dumpfile $HOME/dumpmp3.mp3  &
sleep 30m
kill $!

```

There are several ways to do this :).

Andrew

---

