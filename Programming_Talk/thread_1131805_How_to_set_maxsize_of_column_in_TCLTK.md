---
title: "How to set maxsize of column in TCL/TK ?"
date: 2009-04-21
forum: Programming Talk
---

### Post by tusharv on 2009-04-21
Hi All,

I am working in TCL/TK.

With the help of "grid columnconfigure -minsize" we can configure the min size of the grid. so when the data in that grid exceed the size the size of column grid will increase.

Now the question is can we control the max size of the column ?

If I want only 10 columns in 600x600 geometry with all same size, then how can I get it. and again when data is filled more then size then it should be propagate to next. size should not increase of column.

I have tried with "-uniform" option. It will configure all columns to same size. but if I increase the data size in column, the size of all columns will increase so it will go beyond the 600x600 geometry.

I also have tried with "-minsize" -option. I have made all columns to same size. but again here If the size of data increases in column the particular column size will increase and again it will go beyond the geometry.

So Is there any option to control max size of column and if data size increases then propagate in to next column ?

Thanks,
Tushar

---

### Post by stevescripts on 2009-04-21
> **tusharv said:**
> 
...
So Is there any option to control max size of column and if data size increases then propagate in to next column ?
...


The short answer here is no.

A bit longer answer:

The maximum size of the column ends up being constrained by the way the programmer scripts the widgets and their container.

As far as "spilling-over" data from one column to another - it is the programmer's job, not the widget sets job, to parse the data, and insert it into the GUI.

While it is certainly possible to parse the data so that it "spills-over" from one column to the next,  I would suggest that you seriously reconsider doing so.  What happens to the data in column 10, when one (or more) of the other columns spills over?  

If you have a row of 10 entry widgets, and the data in one of the 10 is longer than the width of the widget,  the data in the widget will scroll.  It is also possible, for example, to bind a procedure to that widget that would pop-up another widget (say a message box for example) that would display the entire contents of the data contained in the entry widget.

While I'm pretty sure that this isn't the answer you wanted to hear, I hope that you somehow find it useful.

Steve

---

