---
title: "[SOLVED] How do I change language settings for a single program?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by mickeelm on 2008-11-29
I'm trying out Gaphor (UML editor, [http://gaphor.devjavu.com/]("http://gaphor.devjavu.com/")) and it seems to be a great tool for my purpose. Though, with a swedish system and swedish language settings, the program menu options etc. are a mix between swedish, english and even dutch. 

I'd like to somehow change some settings resulting in this program always running with english settings, without affecting the language settings for the rest of my system. Is that possible?


EDIT: Problem solved. If anyone has the same problem, here's how it works.

From the terminal, run (gaphor can of course be changed...):

```
LANG=en_US.UTF-8 gaphor
```

If you want this when you launch the program with a program launcher, this should do the trick:

```
sh -c "LANG=en_US.UTF-8 /usr/bin/gaphor"
```

---

