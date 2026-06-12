---
title: "Scite - how to turn on line numbers by default?"
date: 2009-04-21
forum: Programming Talk
---

### Post by eha1990 on 2009-04-21
How do change the SciteGlobal.properties so that "line numbers" are turned on by default when the application is started at any time?

---

### Post by bhagabhi on 2009-04-21
I think the line.margin.visible=1 should be enough, otherwise try setting these:

```

# Sizes and visibility in edit pane
line.margin.visible=1
line.margin.width=5
margin.width=16

```

I have those around line 49 in my SciTEGlobal.properties.

---

