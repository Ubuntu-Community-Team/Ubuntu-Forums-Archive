---
title: "TextView and ScrolledWindow interoperability (Vala)"
date: 2009-11-27
forum: Programming Talk
---

### Post by kumoshk on 2009-11-27
[I have a new question: see my next post.]

In GTK, how do I make my ScrolledWindow scroll to a line of text, by a specific line number of the TextView?

Assume that the TextView is not editable and the cursor is not visible. This needs to be done without regard to font, font size and such, as well.

I need a line to be counted as whenever \n occurs&#8212;not whenever it wraps, too.

I already know how to make it scroll without regard to line numbers, however.

[The answer is to use Gtk.TextIter and the functions relating to it in Gtk.TextView.]

---

### Post by kumoshk on 2009-11-28
New, simpler question:

How do I calculate the number of lines I can see at one time in a Gtk.TextView, in a ScrolledWindow?

I'm needing to make my own Page Down and Page Up functions. The number of lines visible isn't always going to be the same (seeing as font size and such may change). I do need to do it by lines, and not by the scroll value.

---

