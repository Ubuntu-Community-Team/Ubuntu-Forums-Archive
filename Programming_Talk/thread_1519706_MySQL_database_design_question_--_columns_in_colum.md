---
title: "MySQL database design question -- columns in columns?"
date: 2010-06-28
forum: Programming Talk
---

### Post by Cuddles McKitten on 2010-06-28
I've started planning out a database for a website idea I had, but I've got a problem due to my very basic understanding of mySQL.  I don't know what type of data structure to use to put columns in columns of data.  I'm going to have several tables all related to each other, for example:

*TABLE stores* contains column item_list which includes the reference IDs to *TABLE item* which contains the actual data for the items.  My problem is that I don't know how to declare the column item_list so that it can take more than one value, or, in non-database programming speak, declare that as a linked list.  

To further complicate things, I'd like to keep track of things like price history for items, so I'd need some sort of structure like a C struct which would be able to contain both the price and the date together in *TABLE item*.

Does anyone know how to do what I'm doing, or, more likely, have a better suggestion of how to approach this from a mySQL mindset?

---

### Post by GreenN00b on 2010-06-28
Start from here [http://en.wikipedia.org/wiki/Database_normalization]("http://en.wikipedia.org/wiki/Database_normalization") and look at external links too ...

---

### Post by Some Penguin on 2010-06-28
Two approaches that come to mind, assuming that mysql does not yet support a native variable-length array type:

1, instead of storing an entire list with the row, store an identifier that links to another table.  This table will treat this identifier as a NON-unique key -- one row per list node.   You could enforce ordering constraints by using another field if you like.    This may conceivably result in a long table, but you get a fair bit of functionality for this such as the ability to modify or search lists without deserializing/serializing.

2, store the entire list as some serialized blob (not necessarily 'blob' type, a variable-length string would do).  This results in a fat column that is difficult to manipulate.  For instance, asking which row contains a particular item now requires scanning and deserializing every single row with a non-null list blob.    This can also lead to exciting fun if you need to change the serialization format, for sarcastic definitions of 'fun'.

---

### Post by Cuddles McKitten on 2010-06-28
Uh oh.  I must have skimmed something in my books too quickly because that link seems like a non sequitur to me.  The books I've read seemed to have enough info on relational databases and making them work while taking into account errors and inefficiencies.  However, what I'd like to do is convert a two-dimensional array (rows and columns) into a three-dimensional array (rows, columns, and depth).

Does this mean I just have to make table and entries ad nauseum for those attributes and relate them all with keys?  For example, do I need a table like this:

**Store ID**___**Item ID**
1____________110
1____________111
1____________150
1____________161
2____________110
etc.

?  If so, it seems like someone would've implemented what I was hoping for above.

EDIT: Hit post before I saw Penguin's post #3.  Crotch. :(  Looks like I do have to do that, then.

---

### Post by MadCow108 on 2010-06-28
there is the set datatype in mysq which can store more than one value. but it is very limited:
[http://dev.mysql.com/tech-resources/articles/mysql-set-datatype.html](http://dev.mysql.com/tech-resources/articles/mysql-set-datatype.html)

only useful in rare cases but in these it is very convinient.

normalizing is the usual and better way to go for the general case.

---

