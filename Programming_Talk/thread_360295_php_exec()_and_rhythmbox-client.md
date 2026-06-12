---
title: "php exec() and rhythmbox-client?"
date: 2007-02-13
forum: Programming Talk
---

### Post by robinl on 2007-02-13
I've written this little script that gets song info from last.fm and outputs it as a PNG file along with custom skins/colours. Now it's currently running off my computer and I want to add a function that will get the song info directly from rhythmbox-client if the user requested is me (the easy part) as getting it from last.fm is kinda slow. But, the thing is php is not myself, and thus cannot see what I play from
```
rhythmbox-client --print-playing
```

Do I have any other options other than making a little script that writes the song data to a file, put it in crontab and read it in PHP?

---

### Post by lavaramano on 2007-06-16
fsockets() and python (or even bash, i think) will do the trick.

---

