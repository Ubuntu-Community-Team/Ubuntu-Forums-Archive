---
title: "C header problems"
date: 2007-09-04
forum: Programming Talk
---

### Post by astralsin on 2007-09-04
NEVERMIND it was my stupidity and impatience. I was unaware of the correct gcc command provided on that page.  if a moderator could delete this thread, pelase do

> I'm trying to learn GTK programming but I'm having some problems with headers being found at compile time.  I've got gtk.h in /usr/include/gtk-2.0/gtk/gtk.h but when I try to compile the code found on [http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD](http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD) i get the following errors

```
helloworld.c:1:21: error: gtk/gtk.h: No such file or directory
helloworld.c:5: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
helloworld.c:11: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;delete_event&#8217;
helloworld.c:30: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
helloworld.c: In function &#8216;main&#8217;:
helloworld.c:40: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
helloworld.c:40: error: (Each undeclared identifier is reported only once
helloworld.c:40: error: for each function it appears in.)
helloworld.c:40: error: &#8216;window&#8217; undeclared (first use in this function)
helloworld.c:41: error: &#8216;button&#8217; undeclared (first use in this function)
helloworld.c:48: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this function)
helloworld.c:56: error: &#8216;delete_event&#8217; undeclared (first use in this function)
helloworld.c:56: error: &#8216;NULL&#8217; undeclared (first use in this function)
helloworld.c:62: error: &#8216;destroy&#8217; undeclared (first use in this function)
helloworld.c:74: error: &#8216;hello&#8217; undeclared (first use in this function)
helloworld.c:80: error: &#8216;gtk_widget_destroy&#8217; undeclared (first use in this function)

```

is this a problem with Ubuntu's setup or my stupidity?

---

### Post by bashologist on 2007-09-04
It's right on that page.
```
gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
```

---

### Post by LaRoza on 2007-09-04
If it is solved, mark your thread as SOLVED.

---

### Post by astralsin on 2007-09-04
i dont know how to edit the title of the post

---

### Post by bashologist on 2007-09-04
> **astralsin said:**
> i dont know how to edit the title of the post

If you'd like you could select "Thread Tools" then "Mark this thread as solved". Using your browsers find feature should help you find the words easier for your first time. n_n

---

