---
title: "php - deleting a row from a database"
date: 2007-08-14
forum: Programming Talk
---

### Post by woodsonoversoul on 2007-08-14
Hey guys, small problem. I'm trying to write a script that will display rows from a database along with a delete button behind each row. The delete button works (the page updates with the row gone, and works again if I use it on another row) but I get access denied and unable to connect to server errors. This seems wierd seeing as I just connected to the server to remove that row, and, like I said, if I click on another rows delete button it works just fine. What gives?

I think the problem might be in the following section of code (I could be wrong):

[PHP]// if id provided, then delete that record
if (isset($_GET['id'])) {
    // create query to delete record
    $query = "DELETE FROM purchase WHERE sale_id = ".$_GET['id'];
    
    // run the query
    mysql_query($query);[/PHP]

Please keep in mind that I'm using mysqli commands in some parts of the script, could that cause problems?

Any help is greatly appreciated!! Thanks in advance!

---

### Post by Mirrorball on 2007-08-14
A comment unrelated to your question, which I don't know how to answer. Your script is insecure, because it's vulnerable to SQL injection. Someone could set the value of $_GET['id'] to something like "1; DROP TABLE purchase;" and your MySQL server would just drop the table.

---

### Post by slavik on 2007-08-15
would the solution to insecurity be to check for valid id? (isnumber())

---

### Post by Wybiral on 2007-08-15
> **slavik said:**
> would the solution to insecurity be to check for valid id? (isnumber())

I would suggest using "mysql_real_escape_string".

EDIT:

On second look... You're right, even that would leave room for injection. lol. He/she should use the data inside single quotes inside the query string and use the string escape. (that might be their error in the first place, I'm not sure if SQL will accept it outside of single quotes.... I could be crazy though)

---

### Post by Mirrorball on 2007-08-15
If ID is a number, is_number is a good solution. If it were a string, mysql_real_escape_string would do the trick.

---

### Post by Rytmis on 2007-08-15
> **Mirrorball said:**
> A comment unrelated to your question, which I don't know how to answer. Your script is insecure, because it's vulnerable to SQL injection. Someone could set the value of $_GET['id'] to something like "1; DROP TABLE purchase;" and your MySQL server would just drop the table.

That hasn't worked for a while; the PHP MySQL library will only execute one statement per call to mysql_query. However, something like "0 OR TRUE" would expand to 

DELETE FROM foo WHERE id = 0 OR TRUE

which will result in the table being emptied.

[EDIT]

I prefer to use sprintf to force the type, like so (if PDO is not available):

$query = sprintf('DELETE FROM foo WHERE id = %d', mysql_real_escape_string($_GET['id']))

(of course escaping isn't strictly necessary in this context, but I tend to do it anyway lest I slip from the habit)

---

### Post by woodsonoversoul on 2007-08-17
Thanks to all the replies. This is just a personal "nuts and bolts" learning site right now, but as it progresses I'll definitely want to be very secure. Thanks again for all your suggestions.

---

