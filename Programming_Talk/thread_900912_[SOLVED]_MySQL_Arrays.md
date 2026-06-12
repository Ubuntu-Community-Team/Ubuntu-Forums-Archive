---
title: "[SOLVED] MySQL Arrays"
date: 2008-08-25
forum: Programming Talk
---

### Post by themusicwave on 2008-08-25
Hey everyone,

So I volunteered to build a website for a group I was active in, in college.  Part of this is a conference registration page in PHP.  I also need to use MySQL, because the server they got only supports PHP and MySQL.

Does anyone know the SQL sytax to insert data into a text array for MySQL.  I know it for Postgres, but can't find it in MySQL.  I just need the SQL, once I have that I can handle the PHP.

I did some googling, but my brain is kinda tired and I just can't find it.  This is really all I have left for the site.  So please help me out.

Thanks,

Jon

---

### Post by themusicwave on 2008-08-26
I'm surprised that there are no responses.

I'll do some digging tonight and post my solution for future reference.

---

### Post by Xealot on 2008-08-26
Im surprised you didnt find it yourself

[http://se.php.net/manual/en/mysql.examples.php]("http://se.php.net/manual/en/mysql.examples.php")

[http://www.tizag.com/mysqlTutorial/mysqlinsert.php]("http://www.tizag.com/mysqlTutorial/mysqlinsert.php")


Google is your friend

---

### Post by Xealot on 2008-08-26
It seems I might have misunderstood you, Could you specify what exactly you mean by MySQL arrays? or better yet, provide a code sample of how you would do it with PostgreSQL

 - X

---

### Post by themusicwave on 2008-08-26
Hey thanks for the reply.

What I mean is I have a column of datatype text[].  I want to execute a SQL query and put data into thar column.

So I am looking for the syntax of inserting into a text[] datatype.

Such as:

INSERT INTO mytable(someArrayColumn) VALUES(<No Idea What Does Here');

I don't really want to see PHP code.  All I want is the actual SQL.

For some reason every search I do turns up the PHP code.  Also I never seem to be able to find anything about putting things into the text[] column, just getting them out.  I am sure I can get them out, I just don't know the syntax for putting them in.

---

### Post by Xealot on 2008-08-26
> **themusicwave said:**
> Hey thanks for the reply.

What I mean is I have a column of datatype text[].  I want to execute a SQL query and put data into thar column.

So I am looking for the syntax of inserting into a text[] datatype.

Such as:

INSERT INTO mytable(someArrayColumn) VALUES(<No Idea What Does Here');

I don't really want to see PHP code.  All I want is the actual SQL.

For some reason every search I do turns up the PHP code.  Also I never seem to be able to find anything about putting things into the text[] column, just getting them out.  I am sure I can get them out, I just don't know the syntax for putting them in.


I have never heard of being able to have an array datatype in MySQL, Are you sure this even exists?

even so, I dont really see why you would need it, just guessing. And no I havent found anything yet regarding it, hence why im asking :)

---

### Post by themusicwave on 2008-08-26
It does exist, I made a column of type text[].

I need it because I want to store the registrants ethnicity.  It's a bunch of check boxes so they can have multiples.  Like Afircan-American and Asian-American.

I know I could just build a comma separated String, but I just figured it would be nice to learn about the arrays.

Thanks for your interest and trying to help.  I can't really look for it now, I will tonight.

---

### Post by grepgav on 2008-08-27
I'm not sure about the array datatype in MySQL either, but I would store the information in another table.

That is assuming you might later add options or something, so you could have a table that links people to elasticities, and thus you would be able to run reports and comparisons using the table more efficiently than if you wanted to dig through information embedded in text arrays.

String comparisons in general are not desirable due to code efficiency.

---

### Post by themusicwave on 2008-08-27
The idea of another table is a good idea.  Basically I would just link an integer column in the registration table to an int column primary key in the ethnicity table.  Sometimes I like to do this and other times the array may just be simpler.  It all depends on how complex I want the tables to get I guess.  I think using another table is probably better normalization, I took some database classes about 3 years ago, but I forget much...

Good idea thanks!

Also, for those curious I did get it to take my input into the array.  It seems to work similar to Postgres.  I made a String in the format:

'{val1,val2,val3,....,valn}' and send that to the text[] column.  It accepted it, but I have no idea if it is the actual syntax it wanted.  I can't find documentation about it anywhere on the MySQL page or in my PHP and MySQL book....

---

