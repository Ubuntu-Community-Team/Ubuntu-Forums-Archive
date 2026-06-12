---
title: "help with pylab line graph"
date: 2015-08-13
forum: Programming Talk
---

### Post by huff2 on 2015-08-13
I'm trying to run this particular code. The problem is that the graph doesn't actually open up. Can anyone help me with this? Or show me how to make a line graph of this equation, y = x**2? Both would be much appreciated. I'm new to Python so be nice. I'm using Python 2.7.
```
[COLOR=#cc7832]**import **[/COLOR]pylab
[COLOR=#cc7832]**import **[/COLOR]numpy [COLOR=#cc7832]**as **[/COLOR]np
x = np.linspace([COLOR=#6897bb]0[/COLOR][COLOR=#cc7832], [/COLOR][COLOR=#6897bb]20[/COLOR][COLOR=#cc7832], [/COLOR][COLOR=#6897bb]1000[/COLOR])  [COLOR=#808080]# 100 evenly-spaced values from 0 to 50
[/COLOR]y = np.sin(x)

pylab.plot(x[COLOR=#cc7832], [/COLOR]y)
```

---

### Post by steeldriver on 2015-08-13
You need to follow it with a

```

pylab.show()

```

I think?

---

