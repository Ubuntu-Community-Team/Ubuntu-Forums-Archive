---
title: "pygtk button shrink to label?"
date: 2009-12-15
forum: Programming Talk
---

### Post by giuspen on 2009-12-15
Hi,
I need to insert a button (gtk.Button) into the text (gtk.TextBuffer) so I would like the height of the button to match the height of its internal label (that is the same of the external text), but I can't find a way to obtain this result. Around the label there's always the button border and the text line with the button is almost 3 times higher than the others.
Anybody can help me?
I tried also the link button (gtk.LinkButton) but the result is the same as the only difference is that contains an uri.
Thanks in advance.

---

### Post by NoBugs! on 2009-12-26
You can change it with .set_size_request function.
[http://bytes.com/topic/python/answers/42997-pygtk-button-size-question](http://bytes.com/topic/python/answers/42997-pygtk-button-size-question)

---

