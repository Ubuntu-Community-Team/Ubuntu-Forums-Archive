---
title: "Bash script for viewing an image while holding a key"
date: 2012-01-11
forum: Programming Talk
---

### Post by Degran on 2012-01-11
I would like to write a bash script that runs when I press a certain key or a combination of keys and stops when I release the key.
While the key is pressed an image should be shown on my screen and on release should be closed with the script. 

After some searching I suspect the commands "eog" and "read" could come in handy but I'm not even sure if bash is the right choice to create something like this.

Any advice on a part of the problem (doing something while a key is pressed, viewing and closing an image) would be much appreciated.

---

### Post by VCoolio on 2012-01-12
Write a toggle script. What do you use to view your image? If it's imagemagick using display command, something like this:```
#!/bin/bash
if [ $(pidof display) ]; then
  killall display
else
  display /path/to/image
fi
```
Then bind a key / key combo to your script. Now hit the key to start, hit again to stop.

---

### Post by Degran on 2012-01-13
Thank you. That code works great.
Your comment was more help than I expected to get.

---

### Post by VCoolio on 2012-01-14
You're welcome. Remember to mark the thread as solved. Also the same in a oneliner if you want to bind a key directly without the need for a script:```
[ $(pidof display) ] && killall display || display /path/to/image
```

---

