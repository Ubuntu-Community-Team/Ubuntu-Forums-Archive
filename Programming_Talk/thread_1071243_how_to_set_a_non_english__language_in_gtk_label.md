---
title: "how to set a non english  language in gtk label ?"
date: 2009-02-15
forum: Programming Talk
---

### Post by brijith on 2009-02-15
Hai friends,

I have developed a Application using **python + pygtk**. In it all the labels and messages are in** English**. now I want to change it in to a **non English** language. How can I do that in a easy manner. Since I have lots of labels it is difficult to change each of then manually.


[COLOR="DarkOrange"]**Please Help Me**[/COLOR]

[COLOR="DarkOrange"]**Thanks**[/COLOR]

---

### Post by cph05a on 2009-02-24
I've never used python, but here's how you can switch to different character sets in c: [http://www.gtk.org/api/2.6/glib/glib-Character-Set-Conversion.html](http://www.gtk.org/api/2.6/glib/glib-Character-Set-Conversion.html)

---

### Post by cabalas on 2009-02-24
You want to look into gettext, it allows you to translate the strings in applications and display the appropriate language.  Unfortunately after a quick google I couldn't find any good links.

Edit: Perhaps I'm just going blind here is a link to look into [http://docs.python.org/library/gettext.html](http://docs.python.org/library/gettext.html)

---

### Post by kknd on 2009-02-25
The language for the stock icons matchs your locale. If you system is in Portuguese, and you have the translations instaled, it will automatically show the stock icons in Portuguese.

For your text, you can use gettext to do this.
You can switch languages too by forcing a locale change. 

#include <locale.h>

char *setlocale(int category, const char *locale);

---

