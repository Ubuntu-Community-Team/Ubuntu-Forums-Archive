---
title: "Problem using MontyLingua API"
date: 2011-02-25
forum: Programming Talk
---

### Post by jeree on 2011-02-25
Trying to analyse text with MontlyLingua ([2.1]("http://web.media.mit.edu/~hugo/montylingua/#download")), but I encountered some problems.
I'm using Eclipse IDE and I've added montylingua.jar to build path
The code that I'm using is:
```
String raw = "car is blue";
JMontyLingua j = new JMontyLingua();
String jisted = j.jist_predicates(raw); // an example function
```
Which gives output:
```

****** MontyLingua v.2.1 ******
***** by hugo@media.mit.edu *****
Exception in thread "main" Traceback (innermost last):
  File "C:\work\montylingua-2.0\copy\JMontyLingua.py", line 0, in __init__
  File "C:\work\montylingua-2.0\copy\MontyLingua.py", line 0, in __init__
  File "C:\work\montylingua-2.0\copy\MontyLemmatiser.py", line 0, in __init__
IOError: File not found -  (No such file or directory)
```

I'm not very experienced in calling python api form java, but as far as I known the problem here is that those filepaths are hardcoded (or configuratable in a way which I didn't manage to find).
Does anyone have any suggestions how can I use this api in Ubuntu?

---

