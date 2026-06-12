---
title: "Regex File Rename"
date: 2010-06-01
forum: Programming Talk
---

### Post by ided on 2010-06-01
I am trying to wrap my head around regex and how it functions but am running into some issues getting a simple rename to perform the task I need.

I currently have the following filenames (sample)...
Discover_01_hi.mp4
02-Explore_hi.mp4
Discover-03_hi.mp4
(_hi will always be at the end)

I am trying to use rename to essentialy move _hi from the end and put hi_ at the beginning, for example the above filename results would be...
hi_Discover_01.mp4
hi_02-Explore.mp4
hi_Discover-03.mp4

I greatly appreciate any help you can provide.

---

### Post by roccivic on 2010-06-01
Do you have to use regex?

Here's a bash script that does what you want:
```
**[COLOR="Blue"]#!/bin/bash[/COLOR]**
[COLOR="DarkRed"][B]
for [/B][/COLOR][COLOR="Teal"]file[/COLOR][COLOR="DarkRed"]** in **[/COLOR]***[COLOR="DarkRed"]; do[/COLOR]**
[COLOR="DarkRed"]**  if **[/COLOR][ [COLOR="Magenta"]"[/COLOR][COLOR="Purple"]`[/COLOR][COLOR="DarkRed"]**echo**[/COLOR] [COLOR="Teal"]$file[/COLOR][COLOR="Purple"] | [/COLOR][COLOR="DarkRed"]**grep**[/COLOR] [COLOR="Purple"]_hi`[/COLOR][COLOR="Magenta"]"[/COLOR] **[COLOR="DarkRed"]![/COLOR]**= [COLOR="Magenta"]""[/COLOR] ][COLOR="DarkRed"]**; then**[/COLOR]
[COLOR="DarkRed"]**    mv**[/COLOR] [COLOR="Teal"]$file[/COLOR] [COLOR="Magenta"]"hi_`[/COLOR][COLOR="DarkRed"]**echo**[/COLOR] [COLOR="Teal"]$file[/COLOR][COLOR="Purple"] | [/COLOR][COLOR="DarkRed"]**sed **[/COLOR][COLOR="Magenta"]'s/_hi//'`"[/COLOR]
[COLOR="DarkRed"][B]  fi
done[/B][/COLOR]
```

---

### Post by gmargo on 2010-06-01
```

$ rename 's/^/hi_/'          *_hi.mp4
$ rename 's/_hi\.mp4$/.mp4/' *_hi.mp4

```

---

### Post by ided on 2010-06-01
Both answers worked like a charm and I can definitely use both of them.  Thank you guys very much for your help!

---

### Post by sisco311 on 2010-06-01
You don't need two rename commands: 
```
rename -n 's/(.*)_hi.mp4/hi_$1.mp4/' *_hi.mp4
```

---

### Post by ided on 2010-06-02
sisco311-

That worked perfect, thanks for your help as well!

---

