---
title: "Python:using arrays to call and execute files"
date: 2010-01-07
forum: Programming Talk
---

### Post by MikeVaughanG on 2010-01-07
I'm and sort of new to python. 

I have a file with .mp3 files in it , all named 1.mp3, 2.mp3, 3.mp3 etc. 

How do I make an array of the file names, and (using a random number generator, which I've already made) execute the files?

ANy help is very much appreciated.

---

### Post by Can+~ on 2010-01-07
> (using a random number generator, which I've already made)

[PHP]import random

random.randint(0, 10)[/PHP]

Always read the [documentation]("http://docs.python.org/library/random.html") whenever you need a certain feature, it might be (and most of the time is) already created.

> How do I make an array of the file names

How to make a list?

[PHP]playlist = ["filename1", "filename2", "filename3"][/PHP]

If you want to create a list from the files in a certain folder, read on "[listdir]("http://docs.python.org/library/os.html#os.listdir")" in the documentation, for example:

[PHP]#!/usr/bin/env python

import os

folder = "/common/Music/Chris Cornell/2009 - Scream"
plist = filter(lambda filename: os.path.splitext(filename)[1] == ".mp3", os.listdir(folder))

print plist[/PHP]

Produces:
```
['01 - Part Of Me.mp3', '02 - Time.mp3', '03 - Sweet Revenge.mp3', '04 - Get Up.mp3', '05 - Ground Zero.mp3', '06 - Never Far Away.mp3', '07 - Take Me Alive.mp3', '08 - Long Gone.mp3', '09 - Scream.mp3', '10 - Enemy.mp3', '11 - Other Side Of Town.mp3', '12 - Climbing Up The Walls.mp3', '13 - Watch Out.mp3', '14 - Two Drink Minimum.mp3']
```

> execute the files?

Mp3 are not "executed" on their own, you should feed them to another program, let gnome decide (gnome-open), or use a module to play music.

---

### Post by caelestis2 on 2010-01-07
Easier to do
[PHP]
import glob
import random
import os

filelist = glob.glob('*.mp3')
randomtrack = filelist[random.randint(0,len(filelist))]

os.system("vlc "+randomtrack)
[/PHP]

Replace vlc with favorite music program

---

### Post by fiddler616 on 2010-01-07
> **Can+~ said:**
> 

[PHP]
plist = filter(lambda filename: os.path.splitext(filename)[1] == ".mp3", os.listdir(folder))

[/PHP]

Thanks. Whoever says that you can't learn anything by reading about other people's problems is dead wrong.

---

