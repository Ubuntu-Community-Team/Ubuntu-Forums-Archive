---
title: "Is it worth to use a database?"
date: 2006-10-23
forum: Programming Talk
---

### Post by Nonno Bassotto on 2006-10-23
I'm learning to program in Python, and I've come to a point where I need to use a database... at least I think.

I just need to store (locally) some datas about books, like authors, title, language and so on. This should be a first table. A second one should contain a list of folders, and for each one a list of the books contained in it. I should mention that I don't know SQL. Now for the questions.

1) Is it worth the pain to use a database at all, or should I look for a simpler solution?

2) If yes, some search shows that SQLite should be the best solution. But a problem arises: how do I store the info in the second table (folders and books)? It seems to me that there are two ways:
2.1) One column for the folders and one for the books in it, with the book names as an array. Is this allowed? More generally, what kind of data can I put in the tables? Do I need something like pickling to store complex data? Moreover, how do I link the two tables? I'd like to link them by book name.
2.2) A variable size table. Does this make sense at all???

3) Finally, I tried to understand the instructions both for Pysqlite and for Forgetsql. I kinda see how they work, but I'm missing a very basic thing. Both start with the assumption that you already have a database, and you want to interact with it. How do I create one?

---

### Post by spin2cool on 2006-10-23
For a small project, a tab-delimited flat file might be just as easy to use.  (I'm assuming that you don't own tens of thousands or more books).

If you use a database, and if I understand what you want to do correctly, you're making the schema harder than it has to be.  let's use a 4 column example: Unique ID, Title, Author, and Folder.

If you want a list of books that are in a folder, you just use:

SELECT title,author FROM table WHERE folder='asdf'

This returns a list of everything in the 'asdf' folder

---

### Post by DaveBorealis on 2006-10-23
I'm an amateur programmer--it's just a hobby--so take what I say with a grain of salt.  That said, I found using MySQL not that hard to learn with a good book that gave lots of examples showing how to specifically manipulate and store the data.  What you described sounds like a weekend or two project.  I did something similar with MSDS (material safety data sheets) for my science classroom chemical inventory.  It was fun putting the inventory online and writing php scripts to add, delete and modify the data.

A second and more involved option is to store the data in text files, load them into arrays within your program and manipulate the data yourself.  I did this with an online cgi grading program that I wrote in perl...found that fun to do as well!

How many books are you talking about entering the data for?  This might be the determining factor.

Best regards,
Dave

---

### Post by jimscafe on 2006-10-24
I will try to provide my recommendation to your questions.

In a project like this I would almost always start by using text files for the simple reason that while you are developing your prototype you can open the data file with a text editor, you can add data (records) to the text file using the editor and not worry about whether program errors you get are the result of bad sql statements etc.

I agree with the earlier reply, you do not need two tables for this kind of data just columns (fields) for what you need including the folder details.

I would create a class (object) for the book to include all the fields of data you need. If you wish to change the fields, perhaps add one or two, then you can do that quite easily (with the relevant changes to your text file.

Then you can read your text file into an array of these book objects.

To find out which books are in a particular folder is easy - and you could use a list comprehesion to get all the books in one folder.

Write another class to read the text file and create the array (list in python) of table objects. If you later decide to use an sql database, then this would be the only code you would need to change.

```

# Read text file using class booksdb
books = booksdb.read('books.txt')

booksinfolder = [x in books if x.folder = '/novels']

# booksinfolder is now a list of book objects
for bk in booksinfolder:
    print bk.title, bk.author

I have written a class to read a text file like the following :-

ID                Title            Author               Folder
--------------------------------------------------------------------------
978-1-59059-519-0 Beginning Python Magnus Lie Hetland   /data/programming    

It uses the column names to create fields and then parses the data based upon the position of the text relative to the column name

Using tab delimited would give you more freedom with the length of the fields, you cannot use comma delimited because book title might contain commas. I don't like using tabs and would select something else if I decided to use a delimted file - | for example

```

I hope the above make sense.

In answer to if you did use two table how would you link them - using the book name is a bad idea - you need a book ID, either create your own or use the ISBN number that comes with the book. Book titles can easily be miss-spelled and there may even be duplications. Generally using text to link tables is not recommended. (You don't need pickling for this kind of data).

If you are interested in programming I would use an sql database like sqllite once you have got the text version working - the changes should not be much and the experience is good.

To create a table you write
```

conn = sqlite.connect('books.db')
curs = conn.cursor()

curs.execute('''
CREATE TABLE books (
  ISBN        TEXT    PRIMARY KEY,
  title       TEXT,
  author      TEXT,
  folder      TEXT
)
''')
conn.commit()
conn.close()

```

I normally write a simple script to do this as when I am just starting I often want to scrap a table and start again.

---

### Post by Nonno Bassotto on 2006-10-24
> **spin2cool said:**
> For a small project, a tab-delimited flat file might be just as easy to use.  (I'm assuming that you don't own tens of thousands or more books).

If you use a database, and if I understand what you want to do correctly, you're making the schema harder than it has to be.  let's use a 4 column example: Unique ID, Title, Author, and Folder.

If you want a list of books that are in a folder, you just use:

SELECT title,author FROM table WHERE folder='asdf'

This returns a list of everything in the 'asdf' folder

It will be used for something like 3000 books, but I'd like to develop it so that it is possible use more.

For the schema, it is not so easy, since folders will be virtual (I should have mentioned that), so a book will live in multiple folders.

---

### Post by Nonno Bassotto on 2006-10-24
> **DaveBorealis said:**
> A second and more involved option is to store the data in text files, load them into arrays within your program and manipulate the data yourself.  I did this with an online cgi grading program that I wrote in perl...found that fun to do as well!

Yes, but maybe the people writing database know better than me which algorithm is more effective to retrieve data. This is why I thought a database could be better than a text file.

---

### Post by wieman01 on 2006-10-24
Definitely use a database taking into consideration that you have to manage 3000 books and possibly more. I recommend either MySQL or PostreSQL. Both are excellent pieces of software.

This way you won't need arrays or anything in the first place, however, when you read data you may need "objects" in which you temporarily store information, those could also be arrays of objects as well when you want to display your books in a list on the screen.

---

### Post by Nonno Bassotto on 2006-10-24
> **jimscafe said:**
> In answer to if you did use two table how would you link them - using the book name is a bad idea - you need a book ID, either create your own or use the ISBN number that comes with the book. Book titles can easily be miss-spelled and there may even be duplications. Generally using text to link tables is not recommended. (You don't need pickling for this kind of data).

Well, the fact is that within a folder there multiple files, so the second table would contain something like (Folder, Book array). Can I store arrays in the db?

---

### Post by cwaldbieser on 2006-10-24
> **Nonno Bassotto said:**
> 
3) Finally, I tried to understand the instructions both for Pysqlite and for Forgetsql. I kinda see how they work, but I'm missing a very basic thing. Both start with the assumption that you already have a database, and you want to interact with it. How do I create one?

You can create the DB files with command line tools provided with sqlite.
[http://www.sqlite.org/quickstart.html]("http://www.sqlite.org/quickstart.html")

---

### Post by cwaldbieser on 2006-10-24
> **Nonno Bassotto said:**
> Well, the fact is that within a folder there multiple files, so the second table would contain something like (Folder, Book array). Can I store arrays in the db?

Why not just have (Folder, Book) in the second table.  A short sample would be:

```

Folder     Book
--------   ---------
Favorites  UNIX Kung-Fu
Favorites  How to Score One Million Points Playing Pac Man
Favorites  Ender's Game
Computer   UNIX Kung-Fu

```

If you wanted the books from the Favorites folder:
```

SELECT Book
FROM Folders
where Folder = 'Favorites'

```

---

### Post by Nonno Bassotto on 2006-10-24
> **cwaldbieser said:**
> You can create the DB files with command line tools provided with sqlite.
[http://www.sqlite.org/quickstart.html]("http://www.sqlite.org/quickstart.html")

The fact is that my program should create the database. Is there a way to do this?

---

### Post by Nonno Bassotto on 2006-10-24
> **cwaldbieser said:**
> Why not just have (Folder, Book) in the second table.  A short sample would be:

```

Folder     Book
--------   ---------
Favorites  UNIX Kung-Fu
Favorites  How to Score One Million Points Playing Pac Man
Favorites  Ender's Game
Computer   UNIX Kung-Fu

```

If you wanted the books from the Favorites folder:
```

SELECT Book
FROM Folders
where Folder = 'Favorites'

```


Oh, thank you! I'm not really used to think how a database works... :oops: 
Using only tables seems to me such an innatural way to represent the data.

---

### Post by wieman01 on 2006-10-24
> **Nonno Bassotto said:**
> Oh, thank you! I'm not really used to think how a database works... :oops: 
Using only tables seems to me such an innatural way to represent the data.
You're quite right. That why object-oriented databases have become quite fashionable. Sadly relational databases are still dominating for performance reasons. But once you have understood the concept, you'll love them.

---

### Post by bobosity on 2006-10-24
I thought I'd throw this out there:

[http://www.rebol.net/cookbook/recipes/0012.html](http://www.rebol.net/cookbook/recipes/0012.html)

Always more than one way to do it.

---

### Post by cwaldbieser on 2006-10-24
> **Nonno Bassotto said:**
> The fact is that my program should create the database. Is there a way to do this?

Just have your program call the command line tool, maybe?

---

### Post by SlCKB0Y on 2006-10-26
To have this normalised, I think you will need four tables

book, author, folder, bookplacement

Book.
ISBN: Primary key
AuthID: foreign key - > AuthID.author
title
whateverother info you want here

Author.
AuthId: anything (Primary key) (auto-increment)
fname:
initial
lname

folder
folderID - Primary key - anything
folder name
folder description

bookplacement
folderID -> folderID.folder (foreign key)
ISBN -> ISBN.book (foreign Key)
primary key is both these things together.

This layout will allow for the least amount of database errors, redundant data and any other errors associated with an unnormalised database.

---

### Post by SlCKB0Y on 2006-10-26
> **cwaldbieser said:**
> Why not just have (Folder, Book) in the second table.  A short sample would be:

```

Folder     Book
--------   ---------
Favorites  UNIX Kung-Fu
Favorites  How to Score One Million Points Playing Pac Man
Favorites  Ender's Game
Computer   UNIX Kung-Fu

```

If you wanted the books from the Favorites folder:
```

SELECT Book
FROM Folders
where Folder = 'Favorites'

```

Because that layout will result in errors. 

They need 4 tables. They might as well design their DB properly from the start.

---

### Post by Nonno Bassotto on 2006-10-26
> **cwaldbieser said:**
> Just have your program call the command line tool, maybe?

I thought of this possibility, but it doesn't sound quite right. I'll explain better. My program will be a simple desktop application, no dedicated servers, no external database. Think of those apps that organize your music or photo library. Something of that kind with your e-books. So for me a databse is just a convenient way to store some information collected with the  application.
Is there a way to create and open a database using pysql or something of that kind (and without having to rewrite a database app)?

---

### Post by Nonno Bassotto on 2006-10-26
> **SlCKB0Y said:**
> To have this normalised, I think you will need four tables

book, author, folder, bookplacement

Book.
ISBN: Primary key
AuthID: foreign key - > AuthID.author
title
whateverother info you want here

Author.
AuthId: anything (Primary key) (auto-increment)
fname:
initial
lname

folder
folderID - Primary key - anything
folder name
folder description

bookplacement
folderID -> folderID.folder (foreign key)
ISBN -> ISBN.book (foreign Key)
primary key is both these things together.

This layout will allow for the least amount of database errors, redundant data and any other errors associated with an unnormalised database.

Thank you for your advice.

---

### Post by cwaldbieser on 2006-10-26
> **Nonno Bassotto said:**
> I thought of this possibility, but it doesn't sound quite right. I'll explain better. My program will be a simple desktop application, no dedicated servers, no external database. Think of those apps that organize your music or photo library. Something of that kind with your e-books. So for me a databse is just a convenient way to store some information collected with the  application.
Is there a way to create and open a database using pysql or something of that kind (and without having to rewrite a database app)?

Well, depending on your needs, you could use something as simple as the python "shelve" module.  It basically lets you pickle objects in an on-disk dictionary.

SQLite does not seem like a bad way to go for an embedded desktop app if you need to bring the power of SQL queries to the table.  I am not sure why you think invoking the command line tools as a background process "doesn't sound quite right".  Lots of UNIX programs communicate with each other in such a fashion.

There are other "lite" datbase backends that could be considered appropriate for your needs.  The python "gadfly" package is not included in the standard library, but it provides a minimal in-memory database that understands a subset of SQL.

Try to write your program in such a way that you can replace the back end that you use.  That way you can start out with something simple like shelve and then plug in a more sophisticated back end if you feel you need  more flexibility later.

---

### Post by brentoboy on 2006-10-26
I would seriously recommend using a database rather than an alternative file that you write yourself.

Especially SQLite.  I have never programmed SQLite from python, in fact, all my experience with sqlite is in C (on windows).  But, SQLite is a very nice database.

It is not "client-server" so a lot of people knock it, but it doesnt have problems with size, and it can handle multiple processes / PCs all accessing it at once.  And, it is very stable (in my experience)

people are a little prejudice against it because Linux fan-boys like MySQL becuase it is part of the "LAMP stack" and therefore very cool and important, but SQLite is much faster, and it is quite simple really.

I would recommend learning to interact with the database using the command line tool (sqlite is the name of the binary i believe) and just start issuing commands:  Create table BOOKS... insert a few records, and start "selecting" them to see what it returns for you.  Once you get used to adding and retreiving records, you will realize databases are not a layer of complication to add to a program, by instead they are a layer of simplicity -- releaving you of a lot of unneeded headache involved with organizing and mainaining a file that holds all your different data and keeping your memory usage down to only as much as you really need (instead of preloading huge arrays of data just for fun).

---

### Post by Nonno Bassotto on 2006-10-27
> **cwaldbieser said:**
> There are other "lite" datbase backends that could be considered appropriate for your needs.  The python "gadfly" package is not included in the standard library, but it provides a minimal in-memory database that understands a subset of SQL.

Try to write your program in such a way that you can replace the back end that you use.  That way you can start out with something simple like shelve and then plug in a more sophisticated back end if you feel you need  more flexibility later.

Wonderful, gadfly seems exactly what I was looking for. I will consider a separate database when the need arise. Thank you

---

### Post by DavidBell on 2006-10-27
> **Nonno Bassotto said:**
> and I've come to a point where I need to use a database... at least I think.


Have you thought about just doing it in xml and xpath. Has some overhead but the libraries you need will most likely be loaded anyway, and it's not as if sql is lightweight. I think xml would be fine for 3000 or records.

Not sure what the linux equivalent of msxml.dll is but I think tinyxml is cross platform, you can probably use it in python.

DB

---

