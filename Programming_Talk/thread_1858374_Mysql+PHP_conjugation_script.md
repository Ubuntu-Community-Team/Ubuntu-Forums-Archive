---
title: "Mysql+PHP conjugation script"
date: 2011-10-12
forum: Programming Talk
---

### Post by E411 on 2011-10-12
Hola,

I am learning Spanish verbs and at the same time wanted to play around with PHP/mysql. I want to write a script that tests my knowledge: e.g "What is the future of dormir, third person, singular". I don't want to reinvent the wheel but it seemed to me interesting enough while not too complicated.

I am wondering if I'm doing it the right way. In Mysql I created a schema called "verbs" but should I then create one table per verb with one field per form (Present indicative 1st person singular: duermo, Present indicative 2nd person singular: duermes, etc...) or should I rather create one table per tense with one field per person? 

The first option would give me lots of fields but the second lots of tables. Intuitively I would aim at something that could reproduce the logical path of the conjugation: comer > indicative > present > 1st person > singular. But I have the feeling that neither option actually meet that requirement.

---

### Post by Smart Viking on 2011-10-12
I'm not completely sure what you mean, what will output/input look like?

It's a little uncomfortable to advertise for my own projects, but it seems like something like this can be performed with relatively small modifications in the source code of one of my programs, check it out: [http://pugg.smartviking.com/](http://pugg.smartviking.com/)


PS: Unless we are talking about thousands and thousands of questions, you don't really have to use databases, simple CSV files are powerful too.

---

### Post by E411 on 2011-10-12
Hello Smart Viking, yes it is something like your program (thanks for  sharing) but with verbs in Spanish rather than nouns in Norwegian ;)
 
 Joke aside my problem is the following: if I had to work with nouns I would create  one table with the following fields: "word, translation, gender" but the  verbs have several tenses with up to 6 persons for each, which gives me  100 forms for each verb. If I put them in one table that's a lot of  fields and if I create one table per tense it can sum up to hundreds of  tables.

Solution1

Table1: dormir
Field1: duermo
Field2: duermes
Field3: etc...

Table2: tener
Field1: tengo
Field2: tienes
Field3: etc...

Problem: hundreds of fields, how to group them per tense (indicative present, future, etc...)

Solution2

Table1: Dormir - indicative present
Field1: duermo
Field2: duremes

Table2: Dormir - indicative future
Fied1: dormire
Field2: dormiras
Field3: etc...

Problem: hundreds of tables, how to group them per verb (each verb has of course all the tenses)

---

### Post by Smart Viking on 2011-10-12
Why not create a schema for each word in your database?

Just an idea, I'm not skilled with databases.

---

### Post by SeijiSensei on 2011-10-12
I really think a single table with one record per verb and the tense/person combinations as fields makes the most sense.

I'd make the infinitive the primary key for each record.

If you've never used a database in PHP before, I strongly suggest using PostgreSQL rather than MySQL.  While Oracle can't entirely avoid the implications of MySQL being GPL-licensed, I don't trust them to keep it fully free.  I also find Postgres much easier to use and manage, and it hews more closely to SQL syntax standards.

---

### Post by E411 on 2011-10-13
Hey guys,

I thought about it and it is indeed quite overkill to use a database for that. CSV files will definitely do the trick very easily with the php function fgetcsv

I just have one csv file per verb and one line per tense. It works great. Thanks for your help.

(btw if someone knows the answer on how to do it with Mysql I am still interested to know)

---

### Post by E411 on 2011-10-13
Here it is, I have a running script even though it is quite basic (screenshot below).

It reads the directory containing the csv files (one per verb, e.g. "tener.csv") and choses one verb randomly.

Then it reads the file and stores all the forms in one array (one line per tense and one column per person). It draws two random numbers for having a form and this is how the question looks like: "Comer - Future (ellos)"

If you write "comeran" you score one point and get a new question.
If you make a mistake the script gives you the correct answer.

This is it, as I said very basic. Because it is all on one page I had to face a problem with the correction (it took the answer of the current question, not of the previous one) so I had to inject the php variables in the html form like this: 
<input type="hidden" name="score" value="<?php echo $score; ?>" />

If I have time to improve things I would like to store the mistakes so that I can flag the forms and verbs that I don't remember.

Another stuff I have to look at are the accents. So far I just omitted them but it is suboptimal. 

[IMG]http://img707.imageshack.us/img707/2551/spanverbscrsht.png[/IMG]

---

