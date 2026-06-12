---
title: "[GTK] How to use file chooser as cell renderer?"
date: 2010-04-27
forum: Programming Talk
---

### Post by Xhacker Liu on 2010-04-27
I want to use a file chooser as cell render. How to do it?

Thank you!

---

### Post by nvteighen on 2010-04-27
What?

---

### Post by soltanis on 2010-04-27
Is that even a question?

---

### Post by CptPicard on 2010-04-27
In GTK, there are apparently cells... somewhere... and then there is a file chooser component... that he wants to render in this cell. :)

---

### Post by Xhacker Liu on 2010-04-29
There are only CellRendererCombo, CellRendererPixbuf, CellRendererProgress and CellRendererText. But no CellRenderFileChooser!

Help me, thanks!

---

### Post by StephenF on 2010-04-29
> **Xhacker Liu said:**
> There are only CellRendererCombo, CellRendererPixbuf, CellRendererProgress and CellRendererText. But no CellRenderFileChooser!

Help me, thanks!

So you by some miracle get it to render. What makes you think events will propagate correctly from your input devices to the inner widgets?

A FileChooserButton on the other hand, you stand a fair chance with. For one thing, it's cell shaped and is not designed to go invisible when the selection is made.

More here:
[http://faq.pygtk.org/index.py?req=all#13.45](http://faq.pygtk.org/index.py?req=all#13.45)

---

