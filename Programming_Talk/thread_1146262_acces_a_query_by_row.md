---
title: "acces a query by row"
date: 2009-05-02
forum: Programming Talk
---

### Post by Shpongle on 2009-05-02
im doing an assignment and i have to query a database for books and display the results and allow functionality to reserve the books, im mostly using jstl tags on apache tomcat and access in xp in virtual box , (we have to use an access database:( ) any way the search works grand and i have allowed links to reserve where applicable but i need to access each row of the query on screen  

eg when i click reserve beside a row i need to be able to uniquely idenfify that row so i can update the appropriate reserved  row in the database


is there a way i can set a row number or something to reserve details only for that row?

see attached screen for details

---

### Post by s.fox on 2009-05-02
Hi,

Every row has a unique ID number.  You could POST the ID number in the Hyperlink to another script.

Hope this helps.

-Ash R

---

### Post by Shpongle on 2009-05-02
hey how do you find the id no?, the table shown is the results of a search query in a html table and doesnt exist as a table, i entered nothing into the text boxes so it returned all entries, it has to have partial searches allowed so i have to use LIKE , as a result many results can be returned.


it queries 2 tables and displays the results as so. it uses the books and categories tables , 

when i click reserve i have to update the books table and make an entry into the reservations table, 

so if i can find the row no i should be able to get it to work. i know the sql its just i wanna be able uniquely identify each row and use the fields as parameters in the sql update statement.

thanks for gettin back to me :)

---

### Post by kjohansen on 2009-05-02
as ash r said, each row in a table has a primary key, you will need to have this primary key returned in the query.  Since you are querying two tables each table will have a primary key for its entries in the displayed row.

Then you would do 'UPDATE ..... WHERE <SOMETHING_ID>=<selected id>'


<..> means replace with the appropriate name for your table.

---

