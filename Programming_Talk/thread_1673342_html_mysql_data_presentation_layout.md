---
title: "html mysql data presentation layout?"
date: 2011-01-22
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-22
I know this is a big part of the user experience seeing the data in a nice looking format.
I found I can load data in tables, but frankly it looks kludgy.
When the php executes, it basically runs line after line, loads a table which sprawls all over, and the HTML buttons at the bottom of course move all over the page.

What I would like to explore is how to better organize the data on the page.

So, to start, how would you limit the table width?
or how would you put the data in a scrollable window, sort of like a VB list box?
And how would you put a button block on the right side of the page with the table data on the left?

Any good online tutorials or examples to experiment with?

---

### Post by DaithiF on 2011-01-22
Read up a couple of tutorials on CSS layouts.  In particular you'll need to use **div** elements with specified widths and css directives to prescribe how they get laid out on screen.

For advanced grid layouts of tabular data you may eventually want to use a javascript toolkit (e.g. Dojo or YUI).  But you can get a long way with just plain css.

---

