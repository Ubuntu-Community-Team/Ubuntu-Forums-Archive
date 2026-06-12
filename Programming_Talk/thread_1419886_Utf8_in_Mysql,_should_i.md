---
title: "Utf8 in Mysql, should i?"
date: 2010-03-02
forum: Programming Talk
---

### Post by micdhack on 2010-03-02
Hello,
i am creating a website which is going to be multicultural. That means multiple language text to print and text being posted by the users.

In the html <head> i have <meta http-equiv="Content-Type" content="text/html; charset=utf-8"> which works like a charm.

Also anything being posted and stored in the db is being stored correctly cause when i read it back through the mysqli in php is being printed as originally posted.

My mysql text and varchar tables have a latin1_swedish_ci charset.

I am not sure what kind of an effect does the mysql utf8 fields have for the text in the db but so far with the latin1_swedish_ci fields i was able to store Greek, Czech and Japanese letters without problem.

So my question would be, if anything is working correctly, should i change to utf8 or it doesnt really matter?

---

### Post by kahumba on 2010-03-02
In Ubuntu  mysql doesn't default to utf8 which creates troubles when reading Russian strings (unless I encode/decode the strings by hand, which I shouldn't have to).
I've been surprised how the typical Linux distro is almost completely utf8 by default but mysql is not. Somebody is trying to save bytes in exchange for confusion and troubles. Way to go.

---

### Post by The Cog on 2010-03-02
Its my belief that that the mysql tables should be set for utf8 if that's what you're putting in them. Although it might work for now, putting utf8 byte sequences into a latin-1 database table, you may well find later that you want to use tools that are aware of the database encoding and try (correctly) to treat the database contents as latin1 and end up displaying stuff different to what you expect.

---

### Post by Hellkeepa on 2010-03-02
HELLo!

Yes, you should always stick to one charset when manipulating strings in a system. Otherwise you're begging for problems, problems which can be quite annoying in rectifying at a later point in time.

To make sure that your system is UTF-8 all the way through, you need to do the following:
[list=1][*]Send the following header with PHP, or via the web server, on all of the pages displayed:
```
content-type: text/html; charset=utf-8
```
Using the HTML meta tags alone is not enough, as the server overrides these.
[*]Send "USE NAMES 'utf8'" to the MySQL server, right after selecting the database you're using.
[*]Make sure all tables are created with ") DEFAULT CHARSET=utf8;" at the end of the table definition.
[*]Add 'accept-charset="utf-8"' to all form elements in the HTML code.
[*]Make sure you use UTF-8 enabled functions, and actually tell them to use UTF-8, in the PHP source code.[/list]

Happy codin'!

---

### Post by micdhack on 2010-03-03
Wow man thanks! Your answer is perfect and super thorough.
I ll start making the appropriate changes right away.

---

### Post by Hellkeepa on 2010-03-03
HELLo!

You're welcome, glad you found it useful. :-)

Happy codin'!

---

