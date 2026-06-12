---
title: "Another question... Hopefully the last.  QT/C++, how to replace a layout."
date: 2009-01-18
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-18
I have almost finished my project, I now can display almost the entire thing, but unfortunately, I have a table which is too large for my screen, so I have buttons to move through the table.  However, when I press them, I get this message:

QLayout: Attempting to add QLayout "" to Table "", which already has a layout
QWidget::setLayout: Attempting to add QLayout "" to Table "", which already has a layout,

and nothing happens.

I looked through to try to find the command to clear layouts, but I couldn't find it.  So what commands should I use to first check if a layout exists, and then to remove it if it does?

---

### Post by samjh on 2009-01-18
Those error messages look a bit weird.

If my assumption is correct, you have a layout with a table added to it, correct?  Try removing the table from the layout using removeWidget (you can remove layouts using removeItem) and then add the table you want using addWidget.  The layout should update itself, otherwise call update.

---

### Post by Zorgoth on 2009-01-18
I'll take a look at those remove commands, but that isn't exactly the situation.  I have a layout for my whole program, inside which is a Table, which is a widget, inside of which is a grid layout of smaller value-displaying widgets.

---

### Post by samjh on 2009-01-19
Perhaps I'm being obtuse, but why are you using a grid layout within a table instead of just using the cells in the table?

By "table", I presume you mean QTableWidget.  In that case, there is no need for a grid layout.  Give the QTableWidget whatever number of columns and rows you need (setColumnCount and setRowCount, or use QTableWidget(rows, columns, parent) constructor), and set each "smaller value-displaying widget" inside each cell - take a look at the QTableWidgetItem class.

---

### Post by Zorgoth on 2009-01-19
Actually I was designing my own table class, I didn't know there was one.  Is it possible to scroll through the default table if it is too big for your screen?

---

### Post by samjh on 2009-01-19
Yes

---

