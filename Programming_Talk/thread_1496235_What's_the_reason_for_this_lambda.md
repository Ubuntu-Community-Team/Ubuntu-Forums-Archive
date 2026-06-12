---
title: "What's the reason for this lambda?"
date: 2010-05-29
forum: Programming Talk
---

### Post by lavinog on 2010-05-29
Looking at /usr/share/pyshared/pybootchartgui/dray.py:
```

def draw_header(ctx, headers, off_x, duration):
    dur = duration / 100.0
    toshow = [
      ('system.uname', 'uname', lambda s: s),
      ('system.release', 'release', lambda s: s),
      ('system.cpu', 'CPU', lambda s: re.sub('model name\s*:\s*', '', s, 1)),
      ('system.kernel.options', 'kernel options', lambda s: s),
      ('pseudo.header', 'time', lambda s: '%02d:%05.2f' % (math.floor(dur/60), dur - 60 * math.floor(dur/60)))
    ]

    header_y = ctx.font_extents()[2] + 10
    ctx.set_font_size(TITLE_FONT_SIZE)
    draw_text(ctx, headers['title'], TEXT_COLOR, off_x, header_y)
    ctx.set_font_size(TEXT_FONT_SIZE)
	
    for (headerkey, headertitle, mangle) in toshow:
        header_y += ctx.font_extents()[2]
        txt = headertitle + ': ' + mangle(headers.get(headerkey))
        draw_text(ctx, txt, TEXT_COLOR, off_x, header_y)

    return header_y

```
Why bother with the lambda s : s in this line:
```

('system.uname', 'uname', lambda s: s),

```

Edit:
I think I get it now.  It is the mangle function for that key.

---

### Post by simeon87 on 2010-05-29
The point is that you're now passing a function, which will be called when needed. It could be a callback function of some sorts. Take for example a function that transforms a point into a different point.. you could pass a difficult function that does lots of math and gives the point back but you could also give a function that just gives the same point back (i.e., it does nothing). This can be useful because you may not want to alter anything but it is still required that you pass a callable object as argument.

Edit; yeah, in this case it's also called 'mangle' later on. So you want to process it in some way but not all of them need to be modified. However, this is a clean way of separating the code that does the actual work and the list of options. Also, later it's easier to put a different modifying function for one of the options that now has lambda s: s.

---

### Post by StephenF on 2010-05-29
Nitpick: the math.floor calls appear unnecessary as there exists //, the floor division operator which has been in the language for about eight years now.

---

### Post by lavinog on 2010-05-29
> **StephenF said:**
> Nitpick: the math.floor calls appear unnecessary as there exists //, the floor division operator which has been in the language for about eight years now.

also isn't dur - 60 * math.floor(dur/60) the same as dur % 60

---

### Post by StephenF on 2010-05-29
> **lavinog said:**
> also isn't dur - 60 * math.floor(dur/60) the same as dur % 60
Good point.

Neater still.
```

('pseudo.header', 'time', lambda s: '%02d:%05.2f' % divmod(duration / 100, 60))

```
This eliminates the dur = duration / 100 line as well.

---

