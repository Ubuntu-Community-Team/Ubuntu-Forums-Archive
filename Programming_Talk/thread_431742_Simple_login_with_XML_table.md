---
title: "Simple login with XML table"
date: 2007-05-03
forum: Programming Talk
---

### Post by dyous87 on 2007-05-03
Ok here is my question. I have written an xml table including user names and passwords. I want to create a simple login form on an html file that checks the entered user name and password against the xml document. What would be the simplest way to accomplish this using only xml, html and javascript.

Here is my xml table:
```
<?xml version="1.0" encoding="UTF-8"?>

<users>

<userTable>
<user userID="admin" password="leaf4rustle" permission="admin"> admin </user>
</userTable>

<userTable>
<user userID="fordham123" password="ram123" permission="student"> Fordham123 </user>
</userTable>

</users>
```

thanks in advance:
David

---

### Post by LaRoza on 2007-05-03
If you are creating a logon form, something will need to be server side.

Checking names against a document requires you to have a script read the file and find strings, I don't know if ECMAScript can do that, if it can, it won't do it very well. 

PHP, can easily read files (also make, write,append, destroy), and is easy to learn. Python and Perl are also good for this.

If you must use client side technologies, it would be easier to store the names and information in an array and use ECMAScript to loop through it and look for matches, and then create content based on the information, that will not be secure at all, however.

MySQL  + PHP would be better for this.

(I am assuming you are working in a web environment)

---

### Post by dyous87 on 2007-05-03
I know i was thinking that having a javascript code read the xml file would be the simplest way to get something like this done. I want to avoid php and mysql in this. I just am unsure how to get it to work with javascript.

---

### Post by LaRoza on 2007-05-03
Try this, but it seems more complicated than using PHP.

[http://www.expertsrt.com/tutorials/Rod/JSread.php](http://www.expertsrt.com/tutorials/Rod/JSread.php)

You could also use PHP to make files and then read them. You would still have your xml document.

---

