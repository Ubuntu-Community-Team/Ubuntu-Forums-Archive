---
title: "Am I approaching this right?"
date: 2006-12-18
forum: Programming Talk
---

### Post by sailingboarder on 2006-12-18
I am working on a simple project for school, a Latin Study Guide similar to KLatin that's found in the repositories

i am using jdk1.6 and netbeans 5.5

i am planning on using a database to store questions and answers for the study guide, so an embedded database, most likely Derby(JavaDB) since it now comes with jdk1.6

i have stumbled across Hibernate in some of the threads. All I really know about it is that it can remove some of the pain of using java and sql together, but not much else

would Hibernate be appropriate to use in this situation (a simple embedded database), or would it be easier to just do the sql stuff myself?

Any suggestions would be appreciated

---

### Post by pmasiar on 2006-12-18
> **sailingboarder said:**
> I am working on a simple project for school, ... i am using jdk1.6 and netbeans 5.5

Decision to use java is settled, or other language )like python) is negotiable? What was reason to use java? Is it the only language you know?

---

### Post by sailingboarder on 2006-12-19
yes, for this project i am going to use java, for it is the language that i know at the moment

in the future i may learn python or another language, but at the moment, i am going with what i know so that i can finish it on time

plus, i already have a program built, but the storage system is really really basic (static arrays :D ) that was so it would work for a deadline...now i am going back and trying to add either a database or some other kind of storage so the program will be expandable

besides my question of hibernate, would a database in general be the way to go, or would something else like xml or just plain files be better...i know very little to nothing on all three of those, so i'm only looking for the one that would work best

thanks for your comment pmasiar,
i understand this forum is in love with python, but at the moment i don't have time to learn it and finish the project

---

### Post by ohgod on 2006-12-19
I can't help you as far as hibernate goes (I don't actually know java), but...

> **sailingboarder said:**
> 
besides my question of hibernate, would a database in general be the way to go, or would something else like xml or just plain files be better...i know very little to nothing on all three of those, so i'm only looking for the one that would work best


As far as this question goes, I'd recommend a database. Knowing SQL is extremely valuable, and in my opinion using a database in this case would be easier to code than xml or plain text storage methods.

---

### Post by sailingboarder on 2006-12-19
thankyou ohgod, that reassures me on part of my question

i'm going to rephrase my other question to be alittle more specific

will hibernate work in an embedded situation, with embedded derby?

---

### Post by pmasiar on 2006-12-19
> **sailingboarder said:**
> besides my question of hibernate, would a database in general be the way to go, or would something else like xml or just plain files be better...i know very little to nothing on all three of those, so i'm only looking for the one that would work best

How complicated you data structure is? How many tables? complex relations? How much data you have in total: can you load it all into memory at once?

My gut feeling would be against XML. With XML, you have 2 problems: storage **and** parsing.

My best guess would be some simple database libraries, like python's sqlite: no server, just program accesses data (as single user), but using SQL so you can scale up to a real big database like MySQL when you need to. Another option in python would be to build as complicated objects as you need, and pickle them (save to disk) so they are ready to use when needed. 

If you want to use Hibernate or other Object-relational mapper because you are afraid of SQL with complex relations, IMHO you are misguided: if anything go wrong, you have 2 places to look into: SQL, or your misunderstanding of hibernate. It is more problems, not less. Most of java solutions are for big complicated "enterprise-level" problems, and for simpler problems they might be  overkill. 

Try to stay with plain files if you are on deadline and no experience with SQL. Tought call without knowing the details, your experience level and what other local experts you may have access to.

---

### Post by b1g4L on 2006-12-19
For a study guide, it seems the questions and answers would be short enough to just store as plain text. You could stick with your original arrays implementation if you just created a method to count the number of questions/answers (numLines) in the text file first before allocating an array of that size. Then, you can add as many questions/answers to the text file and still maintain an efficient program.

If you don't want to count the number of lines, think of using a linked list possibly.

If you're dead set on using a database, then go for it.....just realize a database isn't really a necessity for this kind of program. Good luck!

---

### Post by sailingboarder on 2006-12-19
if you want details, i shall tell you how my program works now, and then u can tell me your honest opinion of what would work best

right now, i store everything in a two dimensional array, for instance String[][] 

i randomly pick a value for both dimensions, and plug that into a question string
the user answers the question and i compare his/her answer with the value i pulled out of the array

if i needed to, i could possible create class templates for the data, and load/store instances of those classes in the database/file, but i don't at the moment

i am looking for the best thing to work with JAVA, not python or c++ or any other language cause i already know java, and don't have enough time to learn another language
since my database access is so simple, i could learn SQL if need be

---

### Post by pmasiar on 2006-12-19
> **sailingboarder said:**
> i store everything in a two dimensional array, for instance String[][] 
If your database is not too large (fits in memory into your String[][], stay away from databases. As an option, make it arrays first, and **when** runnig and you have time, try version 2.0 with database. But not before it runs in arrays. IMHO.

---

### Post by Tomosaur on 2006-12-20
I had to do a similar project to this not too long ago. My solution was to just store each question as an item in a linked list. This had the disadvantage of not being saved to a hard copy (ie, when the prog was killed, all of the data was lost), but it wasn't part of the spec so it didn't matter anyway - it was more focused on networking and GUI stuff. It wouldn't take very long to save the data to a file and parse it on startup to get it all back into memory or whatever.

If there's no requirement to have the questions persistent, then don't bother. Just use a linked list - it's by far the easiest way to store the Qs, and you can even create objects representing say, topic, or author, and then sort by those fields, while maintining a 'next' and 'previous' functionality.

---

### Post by b1g4L on 2006-12-20
I believe you'll want to maintain the question and answers in a hard copy, so create 2 txt files (questions and answers). I would create 2 arrays - one for questions and one for answers. Count the number of lines (ultimately the number of questions) in the text file, and initialize both arrays of that size (assuming you have the same number answers as questions). To pick a random question, it just becomes a matter of selecting a random number (up to numQuestions - 1). Keep the arrays parallel, so when you're checking the answer to the question you are looking in the same index for both. You probably don't want to ask the same question  twice, so just remove the data from the array after you check to see if the user got it right/wrong. Or, since the arrays have strings in them, set the indexes who's questions have already been asked to -1 or some other int....that makes it easy to check if that question has already occured. Doing it this way, you don't have any unused space...the arrays are the perfect size, and the questions are always expandable because you just add to the text file, and the program will expand the array the correct amount. Hope this helps some...

---

### Post by sailingboarder on 2006-12-20
thankyou everyone for your input

i have decided to use plain txt files, so now i need to go play around with that

if anyone knows a good resource for the java io package i would appreciate that
otherwise, thank's for all you advice, and hopefully i can put it to good use

---

### Post by lloyd mcclendon on 2006-12-21
hibernate is great.  but it takes a decent amount of time before you'll be an expert with it.  i started using it about 4 months ago, i'd say only within the past 3 weeks has it gotten to the point where i don't even think about it anymore.  i've had about 4 different versions of my hibernate infrastructure and the one i've got now is pretty damn good, but i still have some ideas for down the road.

for this project i'd just use jdbc & sql, you'll definately want to know how that works before you can figure out hibernate.  you still have to write queries with hibernate and it's really just a very nice full featured service on top of jdbc.  and the stuff you need to do here is pretty trivial, hibernate really shines when you have a complex object graph with all sorts of relationships.

hibernate can only do so much for you as a persistence service, you are still forced to do a few low level things yourself, like manage the session & transactions.](*,)   fortunately spring helps with that a good bit. 

also the hibernate forum is the _worst_ place on the net if you're looking for answers.  a lot of people have jumped on and most of them are new and only have questions.  and the people that have the answers don't answer anymore cause they don't have anymore questions and have moved on to cooler stuff.

i recommend the book hibernate quickly, that will get you started.  but instead of writing the mapping files or using xdoclet, just go straight to hibernate annotations.  it's 100x easier.  and check out these two articles [http://www.onjava.com/pub/a/onjava/2004/04/07/wiringwebapps.html?page=1](http://www.onjava.com/pub/a/onjava/2004/04/07/wiringwebapps.html?page=1) [http://www-128.ibm.com/developerworks/java/library/j-genericdao.html](http://www-128.ibm.com/developerworks/java/library/j-genericdao.html) & write some python scripts to generate the skeleton code

---

