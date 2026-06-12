---
title: "Bug in gedit's snippets plugin?"
date: 2006-11-24
forum: Programming Talk
---

### Post by prs on 2006-11-24
In gedit there are really useful snippets that can be used when coding. What really baffled me was why I didn't get any when I was in c++-mode.

I looked in /usr/share/gedit-2/plugins/snippets and there was a c++.xml file there.

When I created a dummy snippet inside gedit the snippet was saved in ~/.gnome2/gedit/snippets/c@43@@43@.xml and the title-element in the xml-file also said c@43@@43@ - no wonder the default snippets wasn't loaded. There seems to be some kind of problem with character encodings - either with Ubuntu/Gnome or the snippet plugin.

Am I the only one who experience this behavior? I've been looking around the web, bugzilla and launchpad but noone else seem to be experiencing this.

It's easily solved by copying the original c++.xml to my local directory and renaming it and it's title-element to c@43@@43@. A bit annoying nonetheless.

I'm running Ubuntu Edgy Eft in English but with Swedish keyboard settings.

---

### Post by raporu on 2007-12-20
hey prs

i had the same problem here on gutsy.
I'm running in german.

After searching I found some differences in

```
 grep "language id=" /usr/share/gtksourceview-2.0/language-specs/cpp.lang 
<language id="cpp" _name="C++" version="2.0" _section="Sources">

```
and
```

grep "language"  /usr/share/gedit-2/plugins/snippets/c++.xml 
<snippets language="c@43@@43@">

```

so i changed the line in 
/usr/share/gedit-2/plugins/snippets/c++.xml 
to
```
<snippets language=cpp
```

and this worked for me

---

### Post by samjh on 2007-12-21
Wow, you've just resurrected a 13-months old thread!

Thanks for the tip.  I wondered about this the first time I used gedit for C++ editing. :)

---

