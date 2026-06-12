---
title: "Is SQL really that useful?"
date: 2011-09-04
forum: Programming Talk
---

### Post by aerofly5 on 2011-09-04
I'm a hobbyist programmer and have been for several years now. Usually when I want to store information for a program to use (for example a php login page), I have the usernames and passwods (hashed and salted of course) stored in text files and have the php script iterate through all the entries in the text file until it finds a match. However I have been told that this is a bad habit to get into and that I should just learn SQL (which I find extremely annoying due to syntax). Is this practice really that bad? Is it worth limiting third party software used and effort?

---

### Post by Bachstelze on 2011-09-04
For a simple username/password database, unless you have millions of accounts, a plain text file is perfectly appropriate. It is how your system accounts are stored, for example. SQL is for more complex stuff, for example imagine all the messages and user data of this forum stored in a text file!

---

### Post by NovaAesa on 2011-09-04
SQL becomes really useful when dealing with multiple tables (or **relations** in RDBMS speak). Your scenario only involves a single relation, so SQL would be overkill (although it could possibly improve performance if your DB was big enough). I've worked with systems that have hundreds of tables, doing it from text files would be an absolute nightmare.

---

