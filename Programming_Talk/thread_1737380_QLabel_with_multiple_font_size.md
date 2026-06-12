---
title: "QLabel with multiple font size"
date: 2011-04-23
forum: Programming Talk
---

### Post by Woody1987 on 2011-04-23
I have a QLabel and I want this label to display text with two different font sizes. My current implementation is:

```

ui->titleLabel->setText("<font size=18>text1</font><font size=10>text2</font>");

```

This doesn't work at all. I get two bits of text at the same size, and the size doesn't change regardless of the font sizes I use. A correct example of this would be great.

---

### Post by Vaphell on 2011-04-23
qt4.6.2 and code below works just fine
```
QLabel *testlabel = new QLabel();
testlabel->setText( "<font size=14><b>1111</b></font><font size=20>6666</font>" );
testlabel->setTextFormat( Qt::RichText );
layout->addWidget( testlabel )
```

EDIT: scratch that - it's broken :)

on stackoverflow i found [http://stackoverflow.com/questions/1464591/how-to-create-a-bold-red-text-label-in-qt](http://stackoverflow.com/questions/1464591/how-to-create-a-bold-red-text-label-in-qt)

```
testlabel->setText( "<span style='font-size:18pt; font-weight:600; color:#aa0000;'>text1</span><span style='font-size:10pt; font-weight:600; color:#00aa00;'>text2</span>" );
```

---

### Post by Woody1987 on 2011-04-23
That's it! Thank you.

---

