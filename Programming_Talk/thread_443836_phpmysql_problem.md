---
title: "php/mysql problem"
date: 2007-05-14
forum: Programming Talk
---

### Post by Praill on 2007-05-14
Hello everyone.

I have a form element that uses a textarea and then submits the information to a php script that saves it in a mysql db.
The problem is blank space gets truncated.
Ex. a user types in:
testing
testing
testing

It gets displayed as: testing testing testing.

The php script saves the data in the table in the proper format, but when the query is read back with another php script into a variable and then echo'd out it truncates the blank space.


Im assuming the easiest way to fix this is to get the form to submit in html format (ex. testing<br>testing<br>testing) but Im unsure how to do this without getting the user to write in html format (which is not possible).


Any help would be appreciated. I notice these forums use "get" for the form method instead of "post". Does this have something to do with it?

---

### Post by Mirrorball on 2007-05-14
The nl2br function will convert newline characters to <br>.

---

### Post by kragen on 2007-05-14
Just to expand on what Mirrorball has posted - whats happening is that the php script is in fact echoing out:

> testing
testing
testing

(as you would expect), but in HTML files, new lines don't do anything, and so the displayed html is in fact

> testing testing testing

instead. The nl2br will convert the newline characters into <br> characters.

It's definitely not a good idea to store the text as 

> testing<br>testing<br>testing<br>

in the database - it might work fine for printing back into webpages, but as soon as you want to put that data into anything else, everything would get really messy.

Hope I'm not just stating the obvious here :P

---

### Post by Praill on 2007-05-16
beautiful.. thanks guys.

---

