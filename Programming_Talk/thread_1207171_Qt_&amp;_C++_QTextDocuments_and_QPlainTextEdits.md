---
title: "Qt &amp; C++: QTextDocuments and QPlainTextEdits"
date: 2009-07-07
forum: Programming Talk
---

### Post by JordyD on 2009-07-07
I have a simple problem. When I try to call setDocument on a QPlainTextEdit, it will compile, but during runtime, when I open a file it says: 
```
QPlainTextEdit::setDocument: Document set does not support QPlainTextDocumentLayout
```

Here's the snippet of code that does this:
[PHP]void CodeView::loadFile(QString filename)
{
    QFile file(filename);
    if (file.open(QIODevice::ReadOnly | QIODevice::Text)) {
        QString text = file.readAll();
        QTextDocument document;
        document.setPlainText(text);
        ui->plainTextEdit->setDocument(&document);
    }
    file.close();
}[/PHP]

If I call the setPlainText method on my QTextDocument, should it not already be in QPlainTextDocumentLayout?

Thanks,
Jordy

---

### Post by JordyD on 2009-07-08
bump

---

### Post by JordyD on 2009-07-08
I'm going to post in another forum, as nobody here seems to know. I'll post a link to that post here if I find the answer there.

EDIT: Here's the link, for you Googlers:
[Linky]("http://www.qtcentre.org/forum/f-qt-programming-2/t-qtextdocuments-and-qplaintextedits-22319.html")

---

