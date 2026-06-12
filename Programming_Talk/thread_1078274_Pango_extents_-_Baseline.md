---
title: "Pango extents - Baseline"
date: 2009-02-23
forum: Programming Talk
---

### Post by tom66 on 2009-02-23
I am working with Pangocairo. I need to be able to find out the baseline (line where most glyphs stop, but also the line where the tails of some of the letters such as 'j' and 'y' go) of a particular piece of text, because I am writing a basic layout engine for a project of mine. Any help appreciated. I am currently using 'layout.get_line(0).get_pixel_extents()', but this doesn't give me the baseline.

---

### Post by tom66 on 2009-02-23
Nevermind, solved. If anyone was curious:

```

descent = pango.DESCENT(extents[1])

```

Gets the descent, and the same is true for ascent if you substitute pango.ASCENT with pango.DESCENT. This doesn't give me the baseline, but does give me the descent which can be used to calculate the baseline.

---

