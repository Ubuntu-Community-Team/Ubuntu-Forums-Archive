---
title: "Searching a database"
date: 2010-01-14
forum: Programming Talk
---

### Post by gregarion on 2010-01-14
Hey guys, i have a database which is saved as a text file like this
```
Persia:42:John      ---database
France:50:Mabel 
Persia:50:Rach
Germany:60:John
```
What i am trying to do is to do a search based on two inputs. (1)Title, (2) Author.

```
echo -n "Title:"
read Title  
echo -n "Author:"
read Author

price_check=`awk  -F: '{if ($1== "$Title" && $3== "$Author" ) print $2 } ' fruit`
echo $price_check
```

what i am trying to do is that, when i input for example Persia for $Title and Rach for $Author , i would like the code to print the price and save it into a variable and then display it with the echo command. 

But for some reason, it is not seem to be working, is there something wrong with my coding? 
hope you guys can suggest other ways in which i can do a search with the two input.

---

### Post by stevescripts on 2010-01-14
duh ... lacking time and energy this am, I am not going to exactly answer your question, but offer an alternative solution ...

If you want a database (and your data will increase, and increase your need to write some code for every new output you will need)
start to learn to use a database, SQLite comes to my mind immediately.

I would also suggest that you begin learning something like Tcl or Python, as you *surely will* find you want to run programs and most likely GUIs against your data.

Just my $.02...

Steve
(PS note you will find a lot of help here, especially with Python)

---

