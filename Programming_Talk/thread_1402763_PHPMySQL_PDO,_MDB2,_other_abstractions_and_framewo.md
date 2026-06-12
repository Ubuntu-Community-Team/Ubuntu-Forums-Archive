---
title: "PHP/MySQL: PDO, MDB2, other abstractions and frameworks"
date: 2010-02-09
forum: Programming Talk
---

### Post by bkann on 2010-02-09
Hi -

Please excuse my ignorance on this.  I have been casually writing PHP code for several years now, but I haven't gotten into frameworks or abstraction layers at all.

First, I am confused about the differences between such technologies as MDB2, PDO, and any others available.  What are the differences/advantages/disadvantages, etc., of each?  Why do these exist as different modules?  With my limited knowledge, these two kind of look alike.

Also, even though I reference MDB2 and PDO, I don't honestly know if they're the generally-accepted modules in use today.  Are there newer/better ones I should be aware of?

Next, my understanding is that these abstract my code so that it becomes database/platform-independent.  The SQL queries I have written are still contained within my functions and are rather explicit.  That is, they reference specific tables and fields, as you'd expect.

Is there a way to abstract my database schema so that I can make changes to the database structure and require fewer changes in the code?  For example, is there some mechanism by which I can change a table name or field name and not have to find and correct every instance of it in my code?  Is this where things like CakePHP come in?  I have limited experience with stored procedures... are they an option and to what extent are they used in the industry?

Specifically, my objectives are (1) to write code that can be used across multiple database platforms, (2) to find ways to modify my database schema without breaking my code, and (3) to improve my knowledge and skills as a PHP hobbyist.

I'll be very grateful for any help.  Thanks!

---

### Post by Tibuda on 2010-02-09
> (1) to write code that can be used across multiple database platforms
Both MDB2 and PDO do exactly this. They are substitutes, not complementary. I prefer to work with PDO, but that's an opinion.

> (2) to find ways to modify my database schema without breaking my code
What you are looking for is a new level of abstraction called Object Relational Mapping (ORM). There are some PHP libraries for ORM available out there like [Doctrine]("http://www.doctrine-project.org/") and [Propel]("http://propel.phpdb.org/"). To tell you the truth, I find those PHP ORM libraries are sub-optimal due to PHP restrictions. Rails' ActiveRecord is killer.

CakePHP is not exactly this, it is an implementation of the Model-View-Controller (MVC) framework to separate business logic from presentation. The "Model" here is usually an ORM. Other MVC frameworks for PHP are [symfony]("http://www.symfony-project.org/") and [codeIgniter]("http://codeigniter.com/").

> (3) to improve my knowledge and skills as a PHP hobbyist.
good luck

---

