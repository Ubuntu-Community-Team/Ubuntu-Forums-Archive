---
title: "Strange TreeView issue when selecting rows with mouse"
date: 2009-08-24
forum: Programming Talk
---

### Post by ivanko.rus on 2009-08-24
Hi to everyone! Recently I ran into a weird problem. The part of my program that I am experiencing problems with does the following: it reads some boolean data from the row and based on it sets a checkbutton's state. If the data in rows is different, it sets the checkbutton as "inconsistent". 
    And it actually works very well when I select multiple rows using the keyboard. But when I do the same with mouse (pressing Shift or Ctrl key), it almost doesn't work (only after like 3-unknown times repeating it) :confused:. And the debug output in my program shows that in these cases it only iterates over one row (the count_selected_rows method shows the same), no matter how many I selected. So, that's the problem. I would really appreciate any help. Many thanks in advance! :)

PS  Yes, and I discovered that if I select the items with "rubber band", it works fine. But with "Shift+click" or "ctrl+click" - doesn't work well.
PPS And when I select the rows with mouse (with Shift or Ctrl),nothing happens. But if I click it again, it works. Of course, when selected with Ctrl, the row gets unselected.

---

### Post by ivanko.rus on 2009-08-25
Ok, actually I resolved that problem by connecting the callback to TreeSelection's "Changed" signal instead of TreeView's "cursor-changed" signal. :popcorn:

---

