---
title: "Qt4: Grab text in current line of QTextEdit"
date: 2010-12-01
forum: Programming Talk
---

### Post by Kimm on 2010-12-01
I'm trying to get only the text from the current line in a QTextEdit (i.e. the line the cursor is on), any ideas on how to do this? I have been consulting google for quite a while now without finding any useful information

---

### Post by Kimm on 2010-12-01
Typically, I found the answer shortly after starting the topic...

This is how I got it:
QString text = ui->txtScript->textCursor().block().text().trimmed().toAscii();

---

