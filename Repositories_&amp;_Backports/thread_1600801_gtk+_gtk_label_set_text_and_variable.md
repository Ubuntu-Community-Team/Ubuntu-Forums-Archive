---
title: "gtk+ gtk_label_set_text and variable"
date: 2010-10-19
forum: Repositories &amp; Backports
---

### Post by ementos on 2010-10-19
Hi.
I started to learn GTK in C++ and I have problem with variable.
I want set text of label by text in char variable called zmienna
here is part of my code:
```

#include <gtk/gtk.h>
#include <time.h>
static gchar zmienna;
...

zmienna = 'J';
g_print("%c",zmienna);
gtk_label_set_text(GTK_LABEL(label), zmienna);
```
I saw, that g_print function works, but I'd like to change Label content by the variable. Can you help me?
Greet,
Józek

---

### Post by ementos on 2010-10-19
sorry I made mistake, It should be in another forum "Programming talk"

---

