---
title: "Python: {File &quot;&lt;stdin&gt;&quot;, line 1} error"
date: 2010-08-22
forum: Programming Talk
---

### Post by TejaV on 2010-08-22
Hello everyone,

I've been lurking for past few days, but after doing some research I've settled on Python as my first venture into programming. I've been following some resources around the web and things have been going really well.

However, I've run into a bit of a sticky situation. As of last night, I'm unable to run any of my python scripts. I keep receiving this error:

```
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
```

What baffles me is that the programs managed to run just fine previously, but now none of them seem to run. Any idea?

I apologize if this isn't the proper place to post such a novice question. Any advice would be much appreciated.

P.S - First post!

---

### Post by worksofcraft on 2010-08-22
the >>> prompt indicates you are already running python interpreter.

You need to enter that command from the shell prompt.

Press Ctrl-D to exit Python to the ordinary shell prompt and try again.

---

### Post by TejaV on 2010-08-22
Ah, thank you so much for quick reply. That took care of it!

---

