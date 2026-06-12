---
title: "mplayer and scripting problem"
date: 2011-02-13
forum: Programming Talk
---

### Post by jimwill on 2011-02-13
I posted this on 'absolute beginner' forum with no replies - mods if this isn't allowed, or considered spamming, let me know and I will delete the other thread.

On my ubuntu 10 server I have a script to automatically record (using  mplayer) an internet radio stream and save the file. However, sometimes  I'll get a glitch or something on the stream and the script thinks it's  the end of the feed, at which time it stops recording!
Is there any way I can have the script check the filesize then if it is  too small restart, appending to what is already recorded. That or add a  .1, .2 etc to the end of the filename and cat them together when it has  the full file? Either that or check the time and see if it needs to  continue. 
Or does mplayer have a time-out setting, where I can make it wait a longer time before dropping out?

main recording portion of script
> mplayer -noframedrop -dumpfile /stream/`date +%Y%m%d`/01_`date +%m%d`_filename.mp3 -dumpstream http:ip address &
.
.
script to kill mplayer after given length of time

by the way - these recordings are for myself and not shared on the web! :grin:

---

### Post by andrew.46 on 2011-02-13
Perhaps before you get a complicated script together to check all of these things you might think about adding in a really big cache option to your existing script as well as using the -cache-min option? Something like:

```
-cache 8000 -cache-min 80
```

might be a start...

---

### Post by jimwill on 2011-02-13
Thanks Andrew - I hadn't thought of that,maybe it will work!!! (I don't see, as yet, where it would hurt - the programs are 1 hour long)

---

