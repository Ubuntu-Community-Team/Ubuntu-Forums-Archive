---
title: "Having Many PHP Includes Makes Loading Slow"
date: 2009-05-16
forum: Programming Talk
---

### Post by rizlmilk on 2009-05-16
I own a Pokemon website that I started when I was a kid. Now that I'm off for summer I have some time to work on my PHP, MySQL, etc. My current project is to make a PokeDex, which includes various information on all of the available Pokemon. I have about 100 entries (TMs and HMs) that I want to selectively repeat across over about 500 pages (page for each Pokemon).

I currently have a test page that is listing all of the possible entries. I have about 100 php includes on the test page. The page takes a very long time to load, which I want to fix.

Test page: [http://poke-amph.com/diamondpearl/pokedex/001.php]("http://poke-amph.com/diamondpearl/pokedex/001.php")

Here is an example of one of the included files:
> <tr><td>TM 01</td><td>Focus Punch</td><td>Fighting</td><td>150</td><td>100%</td><td>Physical</td></tr>

Is there a way to make the php include function load pages faster? Or is there a better way to do this, even if it isn't PHP? Could I use databases to do this more efficiently?

---

### Post by MeLight on 2009-05-17
Why not use MySQL to save the info and then fetch it when you need it? If the information you have is already structured (the files you already have are conveniently formatted ) it will be easy to put it in to the database.

---

### Post by s.fox on 2009-05-17
Hi,

I would also say use a database to hold the information.

-Ash R

---

### Post by hessiess on 2009-05-17
Just use a database and a minimal CMS for displaying it. I would also advise you to find a more interesting subject ;).

---

### Post by rizlmilk on 2009-05-17
> **hessiess said:**
> I would also advise you to find a more interesting subject ;).

Lol, I agree. I've had the website forever and I still make money off of it despite the lack of updates. I might as well learn some new technology and increase my chance of earning money at the same time, right? :D

Thanks for the help everyone, I guess I'll start working on databases. Does anyone have a preferred tutorial they could send my way?

---

### Post by mysoogal on 2009-05-17
> **rizlmilk said:**
> Lol, I agree. I've had the website forever and I still make money off of it despite the lack of updates. I might as well learn some new technology and increase my chance of earning money at the same time, right? :D

Thanks for the help everyone, I guess I'll start working on databases. Does anyone have a preferred tutorial they could send my way?


this might help you ! I'm also learning Php With SQL ):P

> [http://php.about.com/od/phpwithmysql/ss/mysql_php.htm](http://php.about.com/od/phpwithmysql/ss/mysql_php.htm)

what you really need, to learn is how to connect to database and insert records into it, and and create a php script which fetches data from mysql, displayed into a table with some css xhtml etc. something like that

look up google for, mysql php tutorials 

:D

---

### Post by hessiess on 2009-05-17
> **rizlmilk said:**
> Lol, I agree. I've had the website forever and I still make money off of it despite the lack of updates. I might as well learn some new technology and increase my chance of earning money at the same time, right? :D

Fair enough ;)

> 
Thanks for the help everyone, I guess I'll start working on databases. Does anyone have a preferred tutorial they could send my way?

The database tutorials at [http://devzone.zend.com/article/627-PHP-101-PHP-For-the-Absolute-Beginner](http://devzone.zend.com/article/627-PHP-101-PHP-For-the-Absolute-Beginner) are pretty good.

I also advise that you look into the Model View Controller(MVC) code structure technique and templateing if you don't already know it, saves having lots of code like:

```

print "<ul>";
foreach($somearray as $line)
{
    print "<li>" . $line . "</li>";
}
print "</ul>";

```

Which can be very hard to maintain and isn't very reusable.

I also recommend that you abstract all of your database assess code into a class, which saves having
oddments of simmaler SQL code scattered all over the place.

---

### Post by rmtatum on 2009-05-17
Are you looking for a tutorial on SQL or using PHP with SQL?

---

### Post by Frak on 2009-05-17
Looks like you're making a basic CRUD (Create, Read, Update, Delete). Add that to you PHP/MySQL vocabulary ;).

[This site]("http://www.w3schools.com/PHP/php_mysql_intro.asp") helped me out when I started with PHP/MySQL.

---

### Post by Reiger on 2009-05-17
> **rizlmilk said:**
> Is there a way to make the php include function load pages faster? Or is there a better way to do this, even if it isn't PHP? Could I use databases to do this more efficiently?

Avoid passing raw HTML to an include if at all possible: this will make the PHP engine pull off an entire circus show just so that you _may_ run PHP code from there. If you know in advance that you will not you can save yourself the overhead of parsing by simply reading out the static content from a file using for instance:
```

echo file_get_contents("my_static.html");

```

---

### Post by rizlmilk on 2009-05-20
Not sure if I should just start a new thread, oh well.

I have started playing around with MySQL and PHP and I am almost done making it extremely easy to finish my project. I just need to know how to do one thing:

> $result = mysql_query("SELECT name, 1, 2, 3, 4, 5, 6, 7, 8 FROM pokemon where name='Turtwig'") or die(mysql_error());
$row = mysql_fetch_array($result);
$count = 1;

while ( $count <= 8 )
{
	echo $count;
	echo $row['$count'];
	$count = $count + 1;
}

The code "echo $row['$count'];" doesn't seem to work. I am trying print out the value associated with 1 through 8 dynamically using the count variable. It works if I manually enter a number like "echo $row['1'];" but I just need to know how to do it with a variable inside.

Thanks for any help.

---

### Post by Reiger on 2009-05-20
Single quoted versus double-quoted strings... Single quoted strings don't do variable substitution: '$count' === "\$count". What you want is either "$count" or plain $count.

---

### Post by rizlmilk on 2009-05-21
If I change it to double quotes or no quotes it just prints out $count, not the information from the table associated with the current number that count is.
It just prints out 1122334455667788 instead of 1*2*3*4*5*6*7*8* (asterisks being values in the table)

---

### Post by Reiger on 2009-05-21
Yes. So? What do you derive from the fact that you don't see what you expect when you echo $row[$count] but get `nothing' instead?

For starters try to echo var_dump($row). I think you'll find a surprise lays hidden there.

---

