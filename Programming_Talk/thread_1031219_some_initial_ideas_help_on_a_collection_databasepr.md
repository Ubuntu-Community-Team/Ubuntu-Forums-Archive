---
title: "some initial ideas help on a collection database/program"
date: 2009-01-05
forum: Programming Talk
---

### Post by MikeSz on 2009-01-05
Hi All,

Ive been learning JavaScript for about a year or so and had an idea for a program that would make my life 10 times easier - I just dont quite know how to do it (programming was never my strong point).

I collect coins and have hundreds of them.  At the moment, they're just stored by type and year but I only have rough paper records as to what ive got.  Ive tried putting it onto a spreadsheet but I have a feeling a quick database program would be more suitable. 

what I would like to do, is write a program whereby I can enter details of all my coins one by one as I sort through them - by type, year, condition, approx value, quantity etc.  and then I can display useful results such as how many coins of a particular type I have, of a particular year etc or for instance show all the pennies in my collection, by year, between say 1920 and 1930.  that way I can have a complete record of what I have and it would make trading them a lot, lot easier.  

I know how to set up arrays, and use 'while' or 'for' loops to search and Ive also become used to setting up forms so that things can be displayed correctly on screen though having had a brief go at this I cant quite get to grips with the different categories for each coin.  for example - I could take a 1920 penny and enter it as a penny (so the more I enter, the more pennies I have) but I cant then add categories, say like the individual year, its condition and its value etc.  

Ive got a feeling this should be a fairly simple program though for some reason I just cant visualise it all fitting together - anyone have any pointers or suggestions that  may help out at all?

---

### Post by mike_g on 2009-01-05
You could avoid programming by using a program for making database such as open office Base.

Or, if youre keen to code something yourself creating a browser app for it would probably be the simplest option. In that case You could use PHP or Python with SQLite. From the sounds of things you should be able to layout you database as a single flat table with columns such as: Name, Year, Condition, Value etc then filter them with simple SQL queries.

---

### Post by pp. on 2009-01-05
I have the distinct feeling that there ought to be an ample selection of ready made applications for this very purpose.

---

### Post by Reiger on 2009-01-05
Like, photo album software?

---

### Post by pp. on 2009-01-05
Like, coin collecting software ?

---

### Post by jesuspresley on 2009-01-05
> **MikeSz said:**
> Hi All,
Ive been learning JavaScript for about a year or so and had an idea for a program that would make my life 10 times easier - I just dont quite know how to do it (programming was never my strong point).


*JavaScript* is a very limited language, and it's not capapble of establishing a database connection. As far as I know, it was only meant to be a extension for missing intarctivity in HTML. As you need some kind of database to store your collection data, JavaScript is out of question. 
[Different thing if in case you were talking about *JAVA*]

> **MikeSz said:**
> Hi All,
Ive tried putting it onto a spreadsheet but I have a feeling a quick database program would be more suitable.
Yes, go for it. Sounds as if you are ready for SQL. 

> **MikeSz said:**
> 
Ive got a feeling this should be a fairly simple program though for some reason I just cant visualise it all fitting together - anyone have any pointers or suggestions that  may help out at all?

Well, you need to combine two things: 
[LIST]
[*]The database format [MySQL,PostreSQL,Firebird SQL,Oracle,etc. ] 
**EDIT: **Storage in XML files is possible too.
[*]And the programming language that creates the user interface - either as a web application or for a local installation[/LIST]

For the database I definitely recommend MySQL - easy to set up, a lot support and very comfortable maintaining software -  PHPMyAdmin or MySQL-Administrator.

The language is a difficult choice. 
[LIST]
[*]Web-based version [i.e. use the application in a browser]:
The quickest solution would be to learn *PHP* or *Ruby on Rails*. If you already know some HTML, you gain success very soon with these easy-to-learn languages. They are platform-independent also, because the scripts run server-based.

[*]Local installation:
If you are looking for an easy graphical programming tool, why not try out [Phoenix]("http://www.janus-software.com/phoenix_screenshots.html") which is a visaual programming language similar to MS Visual Basic. 
I haven't tried it yet, but it might be an easy start.

[*]Also, Java is a very sophisticated language wich can be used very flexible. 

[*]I think Python is rather out of questions due to it's complexity.
[/LIST]

**EDIT:** Have you checked out Tellico: [http://periapsis.org/tellico/?](http://periapsis.org/tellico/?) Maybe this suits your complete needs.

---

### Post by Martin Witte on 2009-01-05
> **jesuspresley said:**
> [LIST][*]Also, Java is a very sophisticated language wich can be used very flexible. 

[*]I think Python is rather out of questions due to it's complexity.
[/LIST]

Flamewar time:)

Java 

```
/*
    Hello.java
    Prints "Hello, World!"
*/

public class Hello
{
    public static void main( String[] args )
    {
        System.out.println( "Hello, World!" );
    }
}

```

versus

Python

```
print "Hello world"
```

---

### Post by jesuspresley on 2009-01-05
Alright, alright. 
Admitted: I was actually just repeating rumors. 
I have never coded in Python, so maybe I should start now ;)

---

### Post by pmasiar on 2009-01-06
> **jesuspresley said:**
> *JavaScript* is a very limited language,...Java is a very sophisticated language ...I think Python is rather out of questions due to it's complexity.


OP, be very carefull when evaluating advice, always ask for second opinion, and check other posts of advisors. Advice above is wrong in so many ways it is not even funny.

JavaScript is weak, yes, but it has libraries to access databases - it is just not used that way, because most often is used to make web page more interactive. jesuspresley is not aware of that. Looks like a case of Java beginner, knowing only one language (Java).

In fact, Python would be excellent language for a beginner like you, OP. But even better would be to spend couple hours looking for such free app, it was likely done by someone. But it would be excellent training task for you if you want to learn programming, and Python would be good start. See wiki in my sig.

---

### Post by MikeSz on 2009-01-06
I think that last idea is a good one.  Im glad in some ways that using JavaScript would be more complex than I had thought.  Ive done plenty of reading into, searching and outputting individual array values - using counters etc to navigate along arrays and just thought that if it was taken one simple step further, I could have an array for each category (such as the coin type, its age etc) and link them up somehow.  It was a simple step in my mind though obviously reality is completely different!!  

Il have a go at python.  I have had a look online for a free program and couldnt see one straight away, though I only did a couple of very quick searches.  Having spent 3 hours last night trying to update all my paper records (and im still not finished) im certainly going to have to get something sorted.  

Thanks for all the suggestions!!

---

### Post by jesuspresley on 2009-01-06
> **pmasiar said:**
> Looks like a case of Java beginner, knowing only one language (Java).

No - no JAVA at all.
I am only coding in PHP. I have not made my way to other languages. But I appreciate your comments, and maybe i will have a sneak into Python.

---

### Post by Zugzwang on 2009-01-06
Actually, most of the solutions posted above look to me like total overkill. 

A simple Excel/OpenOffice Calc/GnuCalc/whatever sheet should do the trick. For the categories, OpenOffice Calc will propose stuff that has been inputted before and you can sort your table by whatever you like, easily export it to HTML if you have a web page, print your list, simple backup, etc.

---

### Post by Martin Witte on 2009-01-06
> **Zugzwang said:**
> Actually, most of the solutions posted above look to me like total overkill. 

A simple Excel/OpenOffice Calc/GnuCalc/whatever sheet should do the trick. For the categories, OpenOffice Calc will propose stuff that has been inputted before and you can sort your table by whatever you like, easily export it to HTML if you have a web page, print your list, simple backup, etc.

OP wants to collect atributes like type, year, condition, approx value, quantity on coins in his collection, and quantities of each coin he has. So to avoid duplication a little database would be optimal. 
> **mike_g said:**
> You could avoid programming by using a program for making database such as open office Base.

Or, if youre keen to code something yourself creating a browser app for it would probably be the simplest option. In that case You could use PHP or Python with SQLite. From the sounds of things you should be able to layout you database as a single flat table with columns such as: Name, Year, Condition, Value etc then filter them with simple SQL queries.
I prefer mike_g s proposal, where I would need at least two tables to avoid duplication: one with table with the attributes - and a primary key, and a table with quantities of the coins, where the foreign key links to the primary key in the attributes table

---

### Post by Achetar on 2009-01-06
OpenOffice Base.

You could also use Django, but I think that would be overkill. Django is UBER EASY (!) but definately overkill.

---

### Post by Achetar on 2009-01-06
> **jesuspresley said:**
> No - no JAVA at all.
I am only coding in PHP. I have not made my way to other languages. But I appreciate your comments, and maybe i will have a sneak into Python.
Give Django + Apache + mod_python a try. djangobook.com is a huge help and python+django is very easy

---

