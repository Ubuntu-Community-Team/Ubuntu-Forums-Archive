---
title: "gtk/pygtk rich text from clipboard (external app)"
date: 2010-12-10
forum: Programming Talk
---

### Post by giuspen on 2010-12-10
Hello,
I'm trying to retrieve rich text information from the clipboard but can't understand the way.
When I paste from an html or openoffice page into my application I see from the available targets also "text/html", but when I request the text contents for that target I get nothing, it seems I can only retrieve text from plain text targets, no way to retrieve html text.
Can anybody give me a clue?
Thanks in advance.

---

### Post by giuspen on 2010-12-10
ok I got it, the problem is that, to retrieve the html data:

selectiondata.get_text() returns None (I was stuck here)
selectiondata.data is the html string

a simple example can be found here: [http://stackoverflow.com/questions/2346924/dump-x-clipboard-data-with-gtk-or-pygtk](http://stackoverflow.com/questions/2346924/dump-x-clipboard-data-with-gtk-or-pygtk)

---

