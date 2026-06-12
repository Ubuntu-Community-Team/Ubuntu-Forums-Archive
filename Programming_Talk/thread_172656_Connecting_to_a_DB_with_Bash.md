---
title: "Connecting to a DB with Bash?"
date: 2006-05-09
forum: Programming Talk
---

### Post by hagen00 on 2006-05-09
Hey 

I want to create a web interface that will allow me to change some variables in a bash script. The easiest way would prob be if I write to a DB from the web and then have my script get the variables from the database...I've done some searching, but so far have found nothing on connecting to a DB with bash. I've done it in Perl before, but I don't want to have to rewrite my script into Perl. 

So can I connect to a DB with a bash script? Is it as simple as just putting 
```
mysql -u name -p password
select * from table
```
The problem is how do you then use those records that are returned?

I could prob also write to text files from the web and then have my script read from those text files. I'll prob do that if i can't connect straight to the DB.

Any thoughts and advice will be appreciated.

---

### Post by yaaarrrgg on 2006-05-09
Ideally, if the script starts getting complex, you'll save more time to rewrite it in a more powerful scripting language like Perl/Python/Ruby.

Although, if you want a quick hack, you don't need to make the script access the database.  Instead, write a seperate web app that writes out a config file (that your bash script reads).  

The only other I would know would be to write an Expect script, and interact with the msql tool.  Might be slow though.

---

### Post by LordHunter317 on 2006-05-09
A DB is the worse way to do this.  I could describe how, but it will be messy. 

I'm in favor of using a configuration file, as yaaarrrgg mentioned.

---

### Post by hagen00 on 2006-05-10
Thanks guys. That's what I"ll do then.

---

