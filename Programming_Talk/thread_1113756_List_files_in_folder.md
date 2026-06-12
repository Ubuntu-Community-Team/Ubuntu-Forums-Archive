---
title: "List files in folder"
date: 2009-04-02
forum: Programming Talk
---

### Post by Vadi on 2009-04-02
Does anyone know a standard command that can list me files in a given folder in this sample output:

```
midori-0.1.5/
midori-0.1.5/midori/
midori-0.1.5/panels/
midori-0.1.5/po/midori.pot
midori-0.1.5/data/
midori-0.1.5/icons/scalable/
midori-0.1.5/icons/16x16/
midori-0.1.5/icons/22x22/
midori-0.1.5/midori/midori-view.c
midori-0.1.5/midori/sokoke.h
midori-0.1.5/midori/midori-extension.c
midori-0.1.5/midori/wscript_build
midori-0.1.5/midori/midori-locationentry.h
midori-0.1.5/midori/midori-stock.h
midori-0.1.5/midori/midori-browser.c
midori-0.1.5/midori/midori-panel.c

```

I read the ls manual, but the closest option I found it "ls --recursive --format=single-column", and that isn't exactly how I need it.

---

### Post by WW on 2009-04-02
If I understand what you want, you could use either **find** or **tree**.
```

find midori-0.1.5

```
or
```

tree midori-0.1.5 -f -i --noreport

```
You might have to install tree first:
```

sudo apt-get install tree

```

---

### Post by Garratt on 2009-04-02
EDIT: you can probably write a fairly simple script: I tried but been far too long since ive done any so i'm not sure.
but something that piped ls through to check if -f or -d then ls -d check again w/e could work...
but tree sounds like it does what your wanting.

---

### Post by Vadi on 2009-04-02
Yes, find it is. I was hoping to use standard provided utilities and not provide my own (packaging mess and etc.).

Thanks!

---

