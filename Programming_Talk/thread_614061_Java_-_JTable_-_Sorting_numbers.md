---
title: "Java - JTable - Sorting numbers"
date: 2007-11-15
forum: Programming Talk
---

### Post by notamonopoly on 2007-11-15
I am fairly new to Java and I've been struggling with using Swing components. I've  learned a lot by reading the docs and following examples but I've hit a wall and it's time to ask some questions.

I have a jTable that has three columns, File name(String), File size(Long) and a Progress (JProgressBar). Ignore the Progress column for the moment, I'm simply trying to get the File size column sorted properly.

I've extended a AbstractTableModel and implemented a TableCellRenderer.

Since the default row sorter sorts everything as a string I made sure to return Long.class in the TableModel getColumnClass() for this column. I thought that would be sufficient but It was still sorting it as a string so I extended the TableRowSorter. 

When I try to add data to the table it gives me a "java.lang.IndexOutOfBoundsException: Invalid range". So I've given up on the TableCellRenderer for the moment and went back to using the default.

I can provide example code if it helps but I mostly wanted to confirm that returning the appropriate class (Long) in the TableModel should cause the default table sorter to sort the column as a number and not a string.

Once I get that working I will tackle extending the TableRowSorter to use for the progress column.

Thank you

---

### Post by notamonopoly on 2007-11-15
I figured it out minutes after creating this thread, isn't that always the way.

I was adding the formatted (DecimalFormat) number to the TableModel so it was treating it as a String, because it was a String. Oops.

---

### Post by JackDog on 2008-03-27
If you are using JTables in Swing, take a look at glazed lists to provide your data bindings. They are bean based and very easy to use. The Glazed Lists supplied TableModel watch your property change listeners and update the table as needed. GL also providessome very powerful and fast filtering/sorting decorations for list - very neat.

---

