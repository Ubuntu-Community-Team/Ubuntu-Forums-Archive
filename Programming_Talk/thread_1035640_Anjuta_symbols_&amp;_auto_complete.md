---
title: "Anjuta symbols &amp; auto complete?"
date: 2009-01-09
forum: Programming Talk
---

### Post by Skerit on 2009-01-09
What do I need for Anjuta to generate tags for python?

I'm finally picking up python in Linux, the first programming language since I was forced to learn VB in school, many years ago. 

It would help out a lot if I had autocompletion functions for pygtk and such.

I got this from the Anjuta website:
> When anjuta is started for first time, it also indexes symbols from all installed libraries for autocompletion and calltips. This provides instant reference to library functions used in the project. The libraries that should be referenced can be selected from symbol browser preferences. 

It skipped this on my machine, I believe. I only see compiz bindings and, after a scan, glib-2.0, libpng, ... All things I'm not directly planning on using.

---

### Post by slavik on 2009-01-10
try:

Edit -> Preferences -> Symbol Browser -> Update Global Tags

---

### Post by Skerit on 2009-01-10
I tried it. Before I did it I only had the compiz tags, now I have glib and libpng and all sorts of others, but no python tags, no sqlite tags, ...

How does it generate them, anyway? From what directories?

---

### Post by Skerit on 2009-01-10
I must say I'm getting quite discouraged. I've spent just about 6 hours now just trying to find an IDE that works decently with python and glade.

Anjuta would be it, but code completion is something I can't live without.

I'm getting the same results on a fresh debian install, so I didn't configure anything wrong.

Is it really impossible to turn of gtksourceview-editor? I read it doesn't support code completion, while scintilla does. I do not understand why you would want to cripple an ide like that :S

---

