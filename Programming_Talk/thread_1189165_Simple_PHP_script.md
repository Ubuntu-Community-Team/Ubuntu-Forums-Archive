---
title: "Simple PHP script"
date: 2009-06-16
forum: Programming Talk
---

### Post by alket on 2009-06-16
Couple of days later a decided to learn Java, but I dont like it, it seems to be very difficult, now I want to learn php, i learned do declare variables and loop, but i need a script to study it for my experimental project.

I need a table with 2 coulmns and when i add something it should be displayed in new row.
in first coulmn to add photo and second to add description
admin panel (no security or password just admin panel) tu add/remove the content.

P.s. dhe datas should be in mySQL

Than you.

---

### Post by Tibuda on 2009-06-16
You should learn PDO to use a database in PHP:
[http://www.php.net/pdo](http://www.php.net/pdo)

---

### Post by Mirge on 2009-06-16
Don't know why you can't just use mysql_query(), mysql_fetch_array() (or mysql_fetch_object()), etc...

---

### Post by markux^Hs on 2009-06-16
[Let Me Google That For You.]("http://lmgtfy.com/?q=php+mysql+tutorial")

---

### Post by Reiger on 2009-06-16
EDIT: Nevermind. Reading the php.net documentation is a good first step, though.

---

### Post by Tibuda on 2009-06-16
> **Mirge said:**
> Don't know why you can't just use mysql_query(), mysql_fetch_array() (or mysql_fetch_object()), etc...

Better use PDO or another abstraction layer. It's a lot easier if you have to switch from mysql to postgresql, than change a lot of files with mysql_* functions.

---

### Post by Mirge on 2009-06-16
> **danielrmt said:**
> Better use PDO or another abstraction layer. It's a lot easier if you have to switch from mysql to postgresql, than change a lot of files with mysql_* functions.

That's true. I've never had to switch to MySQL to PostreSQL yet, so it didn't cross my mind.

---

### Post by ActiveFrost on 2009-06-17
You want to learn php .. why ? You tried Java, you didn't liked it .. looks like you want to be a programmer, just to be a programmer and you've no clue why and what you want to make. Am I wrong ?
Anyway, PHP is for kids - go to tizag.com, learn it from A-Z. After you know the basics, learn some OOP stuff, MVC, Smarty, etc. :)

---

### Post by Reiger on 2009-06-17
PHP is most definitely not *for* kids. That's like saying 'Perl is for kids', 'Python is for kids', 'Bash is for kids'.

I'd suggest you try some 'turtle' as a cure to delusions like that. If your brain survives that, you will know what is for kids (turtle is).

---

### Post by twright on 2009-06-17
I learned a lot of my knowledge of PHP in Wordpress, you could try writing a plugin or looking at other peoples for an easy way of going through the basics. Here is mine, it is not the most elaborately coded thing ever but it does demonstrate server side includes, an ajax style file upload form, creating files on disk and some regular expressions: [http://wordpress.org/extend/plugins/easy-comment-uploads/](http://wordpress.org/extend/plugins/easy-comment-uploads/)

---

### Post by Mirge on 2009-06-17
> **reiger said:**
> php is most definitely not *for* kids. That's like saying 'perl is for kids', 'python is for kids', 'bash is for kids'.

I'd suggest you try some 'turtle' as a cure to delusions like that. If your brain survives that, you will know what is for kids (turtle is).

+1

---

### Post by ActiveFrost on 2009-06-17
> **Reiger said:**
> PHP is most definitely not *for* kids. That's like saying 'Perl is for kids', 'Python is for kids', 'Bash is for kids'.

I'd suggest you try some 'turtle' as a cure to delusions like that. If your brain survives that, you will know what is for kids (turtle is).

Sure, it can't be easy for all of us .. there will always be someone who likes to disagree. I've used PHP for 5 years and have never found it difficult - more likely, boring.
Anyway, that's only my opininion, so .. don't take me too seriously :p

---

### Post by markux^Hs on 2009-06-19
> **ActiveFrost said:**
> Sure, it can't be easy for all of us .. there will always be someone who likes to disagree. I've used PHP for 5 years and have never found it difficult - more likely, boring.
Anyway, that's only my opininion, so .. don't take me too seriously :p

Can you say "*someone's got a chip on their shoulder"*?

---

