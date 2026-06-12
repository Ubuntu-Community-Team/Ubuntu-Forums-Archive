---
title: "Is there a Unicode library to build a text editor on?"
date: 2008-08-09
forum: Programming Talk
---

### Post by deleyd on 2008-08-09
I'm wondering if there already exists, either commercial or public, a core library that handles Unicode, that a text editor could be built on.

So far I'm just looking around at other editors that handle unicode, and if the source is available I'll look at that.

Windows only is OK, however Windows + Linux is even more OK.

What I really want is to build this in layers. I want to first create a language for writing text editors in, (like TPU, but a little different), and I want this language to handle Unicode strings (I don't think TPU handles Unicode strings).

Maybe somewhere is a whole discussion about various methods of designing text editors. Like what various methods are there of storing the text in memory in a way which makes it easy and efficient to add and remove text in a line. Text editors have been around a long time now, I'm sure people have tried various things in the past, and I'd like to learn from the past experience of others. Anyone know of a place where all this is discussed? A website or book?

---

### Post by LaRoza on 2008-08-09
Whatever Gedit uses supports unicode.

---

### Post by nvteighen on 2008-08-09
Have you seen at my "spectacular" GPL'ed Text-Ed? [http://ubuntuforums.org/showthread.php?t=883929](http://ubuntuforums.org/showthread.php?t=883929) (The GUI sucks... and it's absolutely feature-less; it just opens and saves files properly... I'm more a library/backends guy)

GTK+ supports Unicode because it relies on Pango. So, GTK+ may be an option (and it's cross-platform), if you want a GUI program. Its multiline text widget is really nice, If you want a text interface, well, maybe ncursesw (the regular ncurses using multibyte "wide" characters, hence the "w"), but then you restrict it to UNIX and Unix-like systems.

I never have seen a Pango application without GTK+. It should be possible, but it's not common.

---

### Post by kknd on 2008-08-09
glib can handle the most important things (thats why GTK applications are unicode-aware).

If you want more advanced stuff, you can try the great **icu** libray.

---

