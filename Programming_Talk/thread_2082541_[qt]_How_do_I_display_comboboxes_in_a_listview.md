---
title: "[qt] How do I display comboboxes in a listview?"
date: 2012-11-09
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2012-11-09
I am coming from a Gtk background in which I am quite fluent. But I want to contribute something to a project that uses qt and I need to present the data to the user in a certain way.

I want a listview with, let's say, 3 columns. I want the last column to display a combobox in each row, that lets the user select between different values.

In Gtk I would use a GtkCellRendererCombo for that column. What is the equivalent in Qt? Does it have an entirely different approach on how to construct a listview?


(I tried to follow/read the docs, but I got lost. Google doesn't return anything useful for my question.)

---

### Post by SledgeHammer_999 on 2012-11-10
I found my answer. I wanted a QTableView not a ListView. Also one should read the [Model/View Programming](https://qt-project.org/doc/qt-4.8/model-view-programming.html)tutorial. It model/view approach of Qt has some differences from the one Gtk+ uses.

Roughly, the equivalent of the GtkCellRenderer mechanism is the "delegate" mechanism in which you can use any appropriate widget.

QTableView with combobox as delegate example: 
1. [http://programmingexamples.net/wiki/Qt/Delegates/ComboBoxDelegate](http://programmingexamples.net/wiki/Qt/Delegates/ComboBoxDelegate)
2. [https://qt-project.org/wiki/Combo_Boxes_in_Item_Views](https://qt-project.org/wiki/Combo_Boxes_in_Item_Views)

---

