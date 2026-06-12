---
title: "Python 3.1 isn't letting me put in code"
date: 2010-12-08
forum: Programming Talk
---

### Post by WlaadDyaab on 2010-12-08
Hi

I downloaded Python and now I got on Applications "IDLE (using Python-3.1)"

Everything is fine, it's just that I've been going on some YouTube tutorials showing how to do some very straightforward things

I'm trying to do exactly what the guy in the video is doing but I keep getting this:

> [COLOR=Red]SyntaxError: invalid syntax[/COLOR][COLOR=Black]And basically this is what [/COLOR]the guy wrote on Python:

> [COLOR=Orange]print[/COLOR] [COLOR=Green]"Hello, World!"[/COLOR]I don't know if this will help in finding the problem or not but I got my "[COLOR=DarkOrchid]print[/COLOR][COLOR=Black]" in purple color and not in [/COLOR]yellow like it's meant to be.

But my [COLOR=Green]"Hello, World!" [COLOR=Black]is [/COLOR][/COLOR]also in green color, so I don't think there's any problem with that

If someone knows how to fix this problem of "[COLOR=Red]SyntaxError: invalid syntax[/COLOR]" keeping to appear on my Python Shell, please do help!

Thanks!

---

### Post by Zugzwang on 2010-12-08
There are syntactic differences between python 2.X and python 3.X. You are using 3.X but the video you are watching is obviously concerned with 2.X. The syntax of the "print" command has changed between 2.X and 3.X, so you have to use braces now (in 3.X):
```

print("Hello world!")

```

---

### Post by trivialpackets on 2010-12-08
Very true.  I started reading up on python 3.1, but then made a decision to go with 2.x as I was interested in experimenting with django once I got up to speed.  As a result of this decision, I found that the syntax as you noted:

```

print("Whoa!")

```

Works just fine in 2.X as well, so that's what I'm going with so the conversion will be one step easier.  At least if it causes problems, I know the difference.

---

### Post by Quikee on 2010-12-08
> **eric.proctor said:**
> Works just fine in 2.X as well, so that's what I'm going with so the conversion will be one step easier.  At least if it causes problems, I know the difference.

Not only that. If you have python >= 2.6 you can write [PHP]from __future__ import print_function[/PHP] in the beginning of the file and the print function will behave the same as in python 3.

---

### Post by trivialpackets on 2010-12-08
> **Quikee said:**
> Not only that. If you have python >= 2.6 you can write [PHP]from __future__ import print_function[/PHP] in the beginning of the file and the print function will behave the same as in python 3.

On that note, my favorite thing I learned to day was this:

```
from __future__ import braces
```

---

### Post by WlaadDyaab on 2010-12-09
Hey thanks everyone

It's solved now thanks to all of you

---

