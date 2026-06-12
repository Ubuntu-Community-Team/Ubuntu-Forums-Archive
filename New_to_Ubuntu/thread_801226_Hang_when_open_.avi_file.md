---
title: "Hang when open .avi file"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-20
Hello, 

I want to watch movie using TOTEM but unfortunately when I click on the .avi files, my sys hang. I have try every combo possible to escape from this situation:
ctrl+alt+backspace 
ctrl+alt+delete
alt+f2
esc
i have to manually turn off my system. Why this thing happen (i read that ubuntu is very stable and we seldom resort to hard boot our sys in case of such problem). if my combo button is not correct, what is/are the right one?
please assist me. Btw, I'm very sure there's nothing wrong with my .avi because I can play it after restarting.

---

### Post by NT4usB on 2008-05-20
There are a series of keys you can press to safely shut down (if your keyboard is responding) Been several posts on the subject... something about skinny elephants or something.
```
Ctrl+Alt+F1
``` should kick you out to a terminal where you can log in and ```
killall totem
```
Have you tried to wait it out? Sometimes I find video takes a long time (3-4 minutes) to finally choke and give me back control.
Does mplayer give the same problem?

---

### Post by tamoneya on 2008-05-20
try launching it from command line.  That way we should get some descriptive errors.```
cd /directory/where/video/is/
totem myfile.avi
```

---

### Post by NT4usB on 2008-05-20
&& Alt+Tab to bring the terminal back on top of the video so you can read any errors.

---

