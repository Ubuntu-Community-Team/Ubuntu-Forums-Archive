---
title: "update a table in Java..."
date: 2009-04-15
forum: Programming Talk
---

### Post by Mia_tech on 2009-04-15
guys I have a table as part of my gui and the table name is jtable1... the table has 3 columns and 4 rows, with empty spaces.. how could I update the table with new data?... do I have to construct another table and pass the data...

[PHP]JTable jtable1 = new JTable(data, columnNames);[/PHP]

or JTable has a method for updating the table?

---

### Post by simeon87 on 2009-04-15
Sorry, but are you having 'time constraints' like [last time](http://ubuntuforums.org/showpost.php?p=6978224&postcount=3)?

You need to work with a model, like here: [http://www.roseindia.net/java/example/java/swing/InsertRows.shtml](http://www.roseindia.net/java/example/java/swing/InsertRows.shtml)

---

### Post by Neheb on 2009-04-15
You might be able to use the set/getValueAt() methods, but it is a long time since I was working with JTables and I can't find any of my code from that time.

Also you should look at [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/) and use google. Asking in forums should be among the last things you do.

---

### Post by namegame on 2009-04-15
I'd recommend that you look into the "fireTable" methods as well. You may also need to overload the isCellEditable() and setValueAt() methods.

This is all assuming you are wanting to modify the table during runtime.

---

### Post by Mia_tech on 2009-04-16
the method name is "setValueAt"

---

