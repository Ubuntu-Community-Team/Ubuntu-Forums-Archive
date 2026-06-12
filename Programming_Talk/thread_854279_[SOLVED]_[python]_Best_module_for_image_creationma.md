---
title: "[SOLVED] [python] Best module for image creation/manipulation?"
date: 2008-07-09
forum: Programming Talk
---

### Post by durand on 2008-07-09
Hi,
I'm looking for a good image editing library for python. I know about ImageMagick's python bindings and PIL but I'm not sure which one is best for my task.

Basically, I need to overlay one image on top of another, both of which are transparent. I also need to add text to the image. The current script that I've got is written in bash and uses image magick which works really well, but it might be a bit slow...

```
convert -size 140x300 xc:transparent -font Bookman-DemiItalic -pointsize 10 -fill lightblue -draw "text 0,0 '`cat stats.txt`'" stats.png
composite -compose atop -geometry +30+23 stats.png bg2.png trembanner.png

```

Should I continue to use ImageMagick or switch to PIL? I want this application to be as light as possible since it's more of a script than a full blown program.

Thanks!

---

### Post by durand on 2008-07-10
Don't bother replying....I'm going to use PIL.

---

