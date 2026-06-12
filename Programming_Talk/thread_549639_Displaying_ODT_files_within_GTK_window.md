---
title: "Displaying ODT files within GTK window"
date: 2007-09-12
forum: Programming Talk
---

### Post by tonyr1988 on 2007-09-12
To put it simply: I'm needing to create a program using the GTK GUI, and I would like to be able to view an ODT file within the window.

It only needs to be viewable - no editing will be going on. No language is set in stone yet, so most languages will work. Is there any way to do this?

---

### Post by slavik on 2007-09-13
I am pretty sure there is no widget to do this, but I doubt it would be too difficult to do using a language such as perl/ruby/python

ODT is a compressed and an xml file inside of that. you could take that xml, maybe convert the formatting to pango (it looks very much like html) and bam, it's displayed in a textview widget :)

---

### Post by tonyr1988 on 2007-09-13
Cool, I'll have to look more into that.

I forgot to mention that I could also do it using SWT instead of GTK. There doesn't happen to be any widget for SWT, is there?

---

