---
title: "[SOLVED] Need help with installing a module"
date: 2007-11-11
forum: Programming Talk
---

### Post by Interestedinthepenguin on 2007-11-11
I wanted to use "has_value" with my dictionaries, so I downloaded this:  [http://www.radlogic.com/releases/two_way_dict.py](http://www.radlogic.com/releases/two_way_dict.py)

Can anyone tell me what I'm supposed to do with the file?  

...I ran it in the terminal with python; the output was:
```

.......................................
----------------------------------------------------------------------
Ran 39 tests in 0.006s

OK

```

Any help is appreciated.

---

### Post by geirha on 2007-11-12
```
import two_way_dict
help(two_way_dict)
```

Make sure it's either in the directory you run python from, or in /usr/lib/python2.5/site-packages

---

### Post by Interestedinthepenguin on 2007-11-12
Alright! Thank you very much! :)

---

