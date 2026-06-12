---
title: "Need help with python, plasma, and unicode"
date: 2009-09-10
forum: Programming Talk
---

### Post by lykwydchykyn on 2009-09-10
I wrote [ this plasmoid](http://www.kde-look.org/content/show.php/panel-dictionary?content=110707) in python.  Unfortunately, unicode support is totally broken in it, which is kind of bad because it's a dictionary program.

I'm totally stumped on what I did wrong.  I tried adding:
```

#-*- coding: utf-8 -*-

```

to the first line of the script, but it seems to make no difference.  I also tried making all my string literals unicode, and typecasting strings that might be ambiguous to unicode.  But I still get these errors if I enter a string with non-ASCII characters:

```

UnicodeEncodeError: 'ascii' codec can't encode character u'\xdf' in position 15: ordinal not in range(128)

```

Or else I just get no error, and the non-ASCII characters are converted to garbage.

Would anyone be willing to look at the code or give me a pointer here?

---

