---
title: "Geany GTK2 setup"
date: 2010-05-09
forum: Programming Talk
---

### Post by Lex-Man on 2010-05-09
I have installed Geany on netbook and want to try to get some GTK2 development done but when I import the gtk/gtk.h with the line:

#include <gtk/gtk.h>

How do I setup the IDE to use GTK+ and what libraries do I need to install?

---

### Post by blade__tang on 2010-05-29
I have the same question,but I have resolved it. Cause my language version of ubuntu is Chinese, I have to translate the button from Chinese to English. Maybe there will be a littile mistake. Select buile->set buile parameters.

compile:gcc -Wall -c "%f" `pkg-config --cflags --libs gtk+-2.0`
buile:gcc -Wall -o "%e" "%f" `pkg-config --cflags --libs gtk+-2.0`

Then have a try again

---

