---
title: "AWN problems"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Zopiac on 2008-09-05
So i like AWM, but i have two major problems with it:

1. When i log in with AWN starting up automatically, there will be blicks of random junk scattered arounf the screen. Sometimes its duplicates of what AWM looks like, but is usually just grey boxes.

2. When i have Autohide on, it doesnt always autohide, and i have to 'remind' it that it needs to do so by moving the cursor over it >.>

Any fixes? using 0.3.1

---

### Post by anotherdisciple on 2008-09-05
Well... The startup problem can be solved by making a script that delays when AWN starts.

```
#!/bin/bash
sleep 5 #In seconds... feel free to change this
avant-window-navigator &

```

name that file "awn" and put it in your home folder.

then open up a terminal and type this:

```
chmod 755 ~/awn
```

Then go to System > Preferences > Sessions

add a new one that is /home/yourusername/awn

that makes a link to your script...

the script will run at startup and AWN will be delayed by however many seconds you set it for.

Play with that number until you get it to start fast, but not so fast that is causes display issues.

Hope that helps!

---

