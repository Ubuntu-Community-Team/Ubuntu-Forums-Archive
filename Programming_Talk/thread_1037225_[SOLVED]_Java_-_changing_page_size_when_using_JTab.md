---
title: "[SOLVED] Java - changing page size when using JTable Print"
date: 2009-01-11
forum: Programming Talk
---

### Post by ajackson on 2009-01-11
This might just be me having a bad case of "can't google today" but how, if you are using the print method on a JTable object, can you change the page layout (i.e. paper size, orientation, etc).

I'll probably look at the solution and feel totally silly but any help is appreciated.

---

### Post by Zugzwang on 2009-01-12
Have a look at:

[http://java.sun.com/javase/6/docs/api/javax/swing/JTable.html#print(javax.swing.JTable.PrintMode,%20java.text.MessageFormat,%20java.text.MessageFormat,%20boolean,%20javax.print.attribute.PrintRequestAttributeSet,%20boolean,%20javax.print.PrintService](http://java.sun.com/javase/6/docs/api/javax/swing/JTable.html#print(javax.swing.JTable.PrintMode,%20java.text.MessageFormat,%20java.text.MessageFormat,%20boolean,%20javax.print.attribute.PrintRequestAttributeSet,%20boolean,%20javax.print.PrintService))

There something like a "PrintRequestAttributeSet". That looks like the right place to put such information, right? Unfortunately, there's no information on which attributes it contains. However, googling yields:

[http://www.javadocexamples.com/javax/print/attribute/javax.print.attribute.PrintRequestAttributeSet.html](http://www.javadocexamples.com/javax/print/attribute/javax.print.attribute.PrintRequestAttributeSet.html)

---

### Post by ajackson on 2009-01-12
That's what I was looking for thanks. Daft thing is I had looked on the page in the first link, I think my brain was asleep at the time :)

---

