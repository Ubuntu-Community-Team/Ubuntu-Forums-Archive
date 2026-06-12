---
title: "Script help needed"
date: 2008-12-05
forum: Programming Talk
---

### Post by Silvernail on 2008-12-05
Does anyone have any idea why 'feh' would display the first image and then hang up. 'feh' works just fine as a stand alone.

```
#! /bin/bash
mplayer -fs "Llano June 2008"/P6240073.AVI;
mplayer -fs "Llano June 2008"/P6240074.AVI;
feh . --cycle-once --scale-down -r -D 5;

./slideshow.sh;
```

---

### Post by yabbadabbadont on 2008-12-05
What exactly are you trying to accomplish?

---

### Post by Silvernail on 2008-12-05
At a party I want to do a slide show and show a couple short film clips. This needs to repeat over and over for the 4 or so hours the party will last.

I could not find an application that would show images in a slide show and movie clips.

So I rolled my own.

---

### Post by yabbadabbadont on 2008-12-05
```
#! /bin/bash
while true
do
mplayer -fs "Llano June 2008"/P6240073.AVI
mplayer -fs "Llano June 2008"/P6240074.AVI
feh . --cycle-once --scale-down -r -D 5
done

```
There you go.

Just kill the script when you are finished with it.

---

