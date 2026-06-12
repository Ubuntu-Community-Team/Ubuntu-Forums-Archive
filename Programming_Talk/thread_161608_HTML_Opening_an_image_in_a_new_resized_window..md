---
title: "HTML: Opening an image in a new resized window."
date: 2006-04-17
forum: Programming Talk
---

### Post by audax321 on 2006-04-17
Hey,

I just wanted to know if anyone knows of a way to open an image in a new window and then resize that window to fit the image (without any toolbars, etc.) that works on any browser with images of different sizes. I need to finish up my final updates to the website I maintain by tomorrow night so any help is appreciated! If there is no cross-browser way to do this, then I'll just leave this out... but it'd be a nice addition.

Thanks!

---

### Post by nagilum on 2006-04-17
There's a Javascript (who would have guessed ;)) function for this: window.open(). To open a window with a specific size use for example:
```

newin = window.open("file.htm","Title of new window","width=310,height=400");

```
There are more options available, here's a [short reference](http://www.javascripter.net/faq/openinga.htm).

---

### Post by audax321 on 2006-04-17
Thanks, I'll try it out later tonight. :)

---

