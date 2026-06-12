---
title: "MySQL help needed, if anyone has the time?"
date: 2012-07-05
forum: Programming Talk
---

### Post by nikonian on 2012-07-05
Hi there. 


I have just installed Apache2, PHP, PHP MyAdmin + MySQL, and have created a database with a test table and three columns: "id", "username" and "password".

I am struggling, wading through the quagmire of online "reference" material, which, as ever, is DIRECT, specific answers to other people's questions, and not within any form of context.

What I need is some help regards how to POST info to my database and have it store it, and then know how to retrieve it. As usual, YouTube tutorial creators make the fatal mistake of **assuming** the viewer is at the same level of knowledge that they are, and it ends up being a frustrating exercise.

If anyone could spare a few minutes to guide me, my blessings go to you!

Thank you, Matt.

---

### Post by PaulM1985 on 2012-07-06
Ok, so you want to POST to your database.  I am assuming that this is something that you going to do via PHP?

For this you need to learn (if you don't already know) two things:
1 - How to add a row to a database
2 - How POST works

This example shows you how to "INSERT INTO" a database using PHP:
[http://www.w3schools.com/php/php_mysql_insert.asp](http://www.w3schools.com/php/php_mysql_insert.asp)
Looking through all the chapters from here:
[http://www.w3schools.com/php/php_mysql_intro.asp](http://www.w3schools.com/php/php_mysql_intro.asp)
will help you sort out connections to your DB using PHP.

This example will show you how POST works:
[http://www.w3schools.com/php/php_post.asp](http://www.w3schools.com/php/php_post.asp)

You may want to look through everything here: [http://www.w3schools.com/php/default.asp](http://www.w3schools.com/php/default.asp)
I found it really useful when I was learning PHP.

Put those two things together and hopefully you will be flying :-)

Paul

PS - This is by no means using secure connections, which you probably want since you are getting and setting password information, but I recommend you do this for the moment anyway to improve your knowledge before trying more complicated stuff.  I don't know how to do secure stuff, but it is worth knowing the basics first.

PPS - These tutorials are also good for PHP -> MySQL.  This link is to a page preventing SQL injection (people putting un-safe values into your edit boxes with the aim to hack your database): [http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php](http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php)

---

### Post by spamhier on 2012-07-06
Hello yeshuaiseverything,
I am also learning PHP. I agree with PaulM1985: w3schools has good tutorials. It is a fine place to start.
But I have to warn you about their use of the mysql API which is deprecated. The primary source for information is [http://nl.php.net/manual/en/index.php]("http://nl.php.net/manual/en/index.php") . This is what PHP.net says about the mysql API: "[This extension is not recommended for writing new code]("http://nl.php.net/manual/en/intro.mysql.php")".
Instead you should use the mysqli API (MySQL Improved).
So I advise you to first create your test program as proposed by Paul's documentation and when it works, try to rewrite it to mysqli. Here's how to do this: [http://nl.php.net/manual/en/book.mysqli.php]("http://nl.php.net/manual/en/book.mysqli.php").

Regards,
SPamhier

---

### Post by nikonian on 2012-07-06
Thanks folks :) - Yes, I know all about POST and GET methods and PHP interaction with forms etc. Maybe I was just in a funny mood... I managed to hack this together last night, and it works a treat:



#1 - The form:

```
html>
<body>

                <form action="send_data.php" method="post">
                        Username: <input type="text" name="username"/></br>
                        Password: <input type="text" name="password"/></br>
                        DB Name:  <input type="text" name="dbname"/></br>
                        Table Name: <input type="text" name="tablename"/></br>
                <input type="submit" name="submit" value="Send to DB"/>

</body>
</html>

```


#2 -  The handler:

```
<?php

$test_db = mysql_connect("localhost","root","root")
or die (mysql_error());

$username = $_POST['username'];
$password = $_POST['password'];
$dbname = $_POST['dbname'];
$tablename = $_POST['tablename'];

mysql_select_db($dbname, $test_db);

$sql = "INSERT INTO $tablename (username, password) VALUES ('$username', '$password')";

mysql_query($sql, $test_db);

echo "Thanks. </br> Username <h1>" . $username . "</h1> and Password <h1>" . $password . "</h1> have been submitted to MySQL, database name <h3>" . $dbname . "</h3> and table name <h3>" . $tablename . "</h3>";

```

Crude, but I am a newcomer, and it worked... and brought a GRIN to my face! :D

Thank you again, blessings to all.

---

### Post by epicoder on 2012-07-06
Please, please, PLEASE stop using and recommending W3Schools as a resource! See the link in my signature for the reason why. In short, they teach you to produce TERRIBLE code, their certifications are questionable at best, and they are NOT affiliated with the W3C in any way.

You've got a start- However, there are a number of problems with your code. 
[LIST=1]
[*]You forgot the starting angle bracket on html. <html>, not html>.
[*]You are missing the <head> and <title> elements which are both required.
[*]<input> elements must be inside flow elements. <div> will work in a pinch.
[*]There's no doctype- Quirks mode ahoy! (Google for explanation, low on time here) <!DOCTYPE html> will work in most modern browsers.
[/LIST]

---

### Post by nikonian on 2012-07-06
> **sh228 said:**
> Please, please, PLEASE stop using and recommending W3Schools as a resource! See the link in my signature for the reason why. In short, they teach you to produce TERRIBLE code, their certifications are questionable at best, and they are NOT affiliated with the W3C in any way.

You've got a start- However, there are a number of problems with your code. 
[LIST=1]
[*]You forgot the starting angle bracket on html. <html>, not html>.
[*]You are missing the <head> and <title> elements which are both required.
[*]<input> elements must be inside flow elements. <div> will work in a pinch.
[*]There's no doctype- Quirks mode ahoy! (Google for explanation, low on time here) <!DOCTYPE html> will work in most modern browsers.
[/LIST]


That "<" is there in the code - I must have missed it when c/p in vi. 

I get the point about <head> and  <title>, thanks.

The <input> elements ARE inside... the form is closed by the submit element, or am I wrong? A tutorial I watched, showed it this way...

---

### Post by trent.josephsen on 2012-07-06
That tutorial was wrong, you need to close the form with a </form> tag just like everything else, and <input> is an inline element; you have to put it directly inside a block element. <form> is a block element, but for purposes of nesting it doesn't count, IIRC. (<blockquote> is the same way; you can't put inline elements or text directly inside a <blockquote>.) Somebody correct me if I'm wrong.

---

### Post by SeijiSensei on 2012-07-06
> ```
$dbname = $_POST['dbname'];
$tablename = $_POST['tablename'];
```

I don't want to get too deep into this discussion, but the lines you posted are a very bad practice for security reasons.  You definitely do not want to put any of the database information in the form.  Users should only be able to enter the absolute minimum amount of information required to perform a task.  Everything else, particularly anything related to the database, should be locked away inside the script.  You should also perform sanity checks on user input so attackers cannot try and use "SQL-injection" methods to extract information from the database they shouldn't see.

---

### Post by PaulM1985 on 2012-07-06
> **sh228 said:**
> Please, please, PLEASE stop using and recommending W3Schools as a resource! See the link in my signature for the reason why. In short, they teach you to produce TERRIBLE code, their certifications are questionable at best, and they are NOT affiliated with the W3C in any way.

I think I have been told off :-)

---

### Post by wojox on 2012-07-06
> **PaulM1985 said:**
> I think I have been told off :-)

By a troll. :p

---

### Post by epicoder on 2012-07-06
> **PaulM1985 said:**
> I think I have been told off :)
I'm sorry if I came off that way, I'm just frustrated with a multitude of things at the moment- the least of which is W3Schools fooling people with terrible information. I'm not trying to tell you off in any way, I'm telling W3Schools off.

> **wojox said:**
> By a troll. :p
I am not trolling- please read the link in my signature as to why I tend to get frustrated when people mention W3Schools. If anyone, W3Schools are the trolls.

See trent.josephsen's post for a much better explanation of my 3rd point, I did end up being a bit terse there. The idea is that text has to be contained within what is known as a *flow* element, such as <p> or <div>. Raw text and <input> elements that are direct children of form elements are invalid.

---

### Post by PaulM1985 on 2012-07-07
> **sh228 said:**
> I'm sorry if I came off that way, I'm just frustrated with a multitude of things at the moment- the least of which is W3Schools fooling people with terrible information. I'm not trying to tell you off in any way, I'm telling W3Schools off.

No worries, I put a :-) next to it because I was only saying it a bit tongue in cheek.

It is funny how threads can influence you... after reading this I went off and made a mailing list for my website.  Yesterday was productive.

Paul

---

### Post by nikonian on 2012-07-07
I avoid this forum as much as possible for the very things happening in this thread: egotistical in-fighting.

Thanks for the help guys, I'll see you in another 6 months.

---

### Post by lykwydchykyn on 2012-07-07
> **yeshuaiseverything said:**
> I avoid this forum as much as possible for the very things happening in this thread: egotistical in-fighting.

Thanks for the help guys, I'll see you in another 6 months.

You may see egos and infighting, but I see people who don't want an aspiring programmer to get off on the wrong foot and learn lessons the hard way.  

The code you posted will work, but if you use that on a public website, you'll get hacked.  I'd hate to see that happen to anyone.  

The easiest way to avoid this is not to use the mysql_connect or mysql_query functions, but to use the newer and more secure PDO interface for PHP.  It allows you use prepared queries, and takes care of properly escaping your data for you.  See this page for how to use it:

[http://php.net/manual/en/book.pdo.php](http://php.net/manual/en/book.pdo.php)

Hope that helps.

---

### Post by nikonian on 2012-07-07
> **lykwydchykyn said:**
> You may see egos and infighting, but I see people who don't want an aspiring programmer to get off on the wrong foot and learn lessons the hard way.  

The code you posted will work, but if you use that on a public website, you'll get hacked.  I'd hate to see that happen to anyone.  

The easiest way to avoid this is not to use the mysql_connect or mysql_query functions, but to use the newer and more secure PDO interface for PHP.  It allows you use prepared queries, and takes care of properly escaping your data for you.  See this page for how to use it:

[http://php.net/manual/en/book.pdo.php](http://php.net/manual/en/book.pdo.php)

Hope that helps.

Thank you :D

---

