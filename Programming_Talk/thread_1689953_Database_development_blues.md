---
title: "Database development blues"
date: 2011-02-17
forum: Programming Talk
---

### Post by TpwUK on 2011-02-17
Hi guys, need help again ... I am after a simple DB front end for creating field-names, types lengths etc, but i seem to have ran into a brick wall and can't find anything. Tried Openoffice & Libreoffice and they can't export to *.db.

I don't want to be using any SQL DBMS, i want to use Berkeley DB so i wont have to make any server connections, the database does not need network support, and it wont be accessed by more than one user at a time so need for a managing system.

Is there a database design tool that can just export a *.db ??

Any help appreciated
TpwUK

---

### Post by thornmastr on 2011-02-17
Have you looked at SQLITE.  [http://www.sqlite.org/](http://www.sqlite.org/)

It sounds to be what you might want to pursue.

HTH,

Thorny

---

### Post by TpwUK on 2011-02-17
SQL is not required, for the size of the database it would be like taking a sledge hammer to a pecan ... But thanks for the speedy reply

;)

TpwUK

---

### Post by thornmastr on 2011-02-17
Arggggggggg!


Yyour reply suggests to me you saw 'SQL' and shut your mind like a steel trap. Think Lite. Think a receptacle to push things in and pull thing out. Realize its got no server. It's not multi processing, not multi serving. Its One user one file but you call the file a DB. You actually use rather standard SQL constructs to manipulate the data which really standardizes your file description. Take 10 minutes and read the introduction. If you still feels it's a sledge hammer,well.....OK....it's been fun needling your sensibilities and hopefully you've enjoyed doing the same,but if, by some small chance it really does meet your needs, I would be delighted. No, I'm not involved with the project. I just enjoy using it; and I enjoy seeking our converts.

Thorny

---

### Post by TpwUK on 2011-02-17
Sorry thornmastr i did not mean to offend you. I have looked at SQL DBM tools and i too like them and their abilities, and i am open minded, i have no doubt that at some stage i may need SQL further into my pet project but for a simple contacts/suppliers database SQL is overkill.

Berkeley DB promotes itself as having an SQL c++ library that is very close to SQLite3  and if i understand things correctly ... which at my age and experience levels becomes harder each passing year ... By using BDB you remove the overhead of parsing the SQL queries as the whole is built into your application removing the need for database management engines/servers and no 3rd party stuff like Interbase etc

If i am wrong then feel free to toast me alive, I just seem to be frustrating myself with the wealth of information that is out there, but it all seems to be SQL based, All i need is a simple front-end gui to design a simple field/value database that saves the file as a  *.db and complies to the BDB format

Hope that all makes sense :confused:

TpwUK

---

### Post by Some Penguin on 2011-02-17
You've already made the decision to use a crude key/value store which basically treats values as untyped byte blobs, so it's completely up to you to decide how to serialize and deserialize your records into those byte blobs. Have fun.

---

### Post by TpwUK on 2011-02-17
Agreed Penguin ... but all i am looking for is a table design tool that will save the structure as an empty *.db just like you get in any database tool like Openoffice MSOffice etc etc

Maybe i ask too much ... Borland used to provide such wonderful tools with Delphi and C++ Builder so you could draft up the db structure and then just get on with the visual side of your app. Showing my Windoze roots i guess

TpwUK

---

### Post by StephenDavison on 2011-02-17
> **TpwUK said:**
>  ... By using BDB you remove the overhead of parsing the SQL queries as the whole is built into your application removing the need for database management engines/servers and no 3rd party stuff like Interbase etc


You still did not pay attention to thornmastr's points regarding SQLite.  Try to get over the idea that SQL implies complexity and client/server architecture.  

It looks like [http://en.wikipedia.org/wiki/SQLite_Manager](http://en.wikipedia.org/wiki/SQLite_Manager) may fit your bill.

---

### Post by TpwUK on 2011-02-17
Thanks for the reply Stephen, i went to have a look  and copy it back here for easier discussion.

[HTML]SQLite Manager is a SQLite database manager provided as a Firefox extension.  
By providing the software as a Firefox extension, SQLite Manager is  available on many different platforms and trivially easy to install. As  well as being provided as a Firefox extension it's also available for a  few other environments.
  It allows the user to:
  View the contents of one or more SQLite databases.Manage tables, indexes, views and triggers.View and manage the records.Build an SQL query and execute it.Export data to CSV or XML. [/HTML]


A firefox extension ... Cool but not needed adds dependencies
View lots of SQLite DB's - nope not needed by my app
Manage tables, indexes and views - hell yeah, but for BDB
View and manage the records - Thats the job of my app and its database gui
build and execute SQL query - not needed by my app
export csv or xml - nice, but again not needed by my app


Just a simple BDB Table design tool is all i need, I am a simple gardener. not a pro IT guy or a developer, so maybe my terminology or description is wrong and confusing things. The tool i was referring to with Delphi and C++ Builder was a really crude tool, not pretty just functional ... Select your database model type; Oracle, DB, DB2 etc and then just enter the fields, their type and size where applicable and what you wanted to call the database, quick and easy ;)



TpwUK

---

### Post by Some Penguin on 2011-02-17
There IS NO DATABASE STRUCTURE.  There are no tables.   There are no columns.  It's key-value.  Period. 

You're basically asking for a tool to generate your entire data access layer (CODE, not simple schema descriptions) including your structures.  Or for a library to provide an abstraction layer.  This is not Delphi, it's Berkeley DB.   The .BDB will NOT contain a schemata description that other BDB clients can interpret unless they're using the same abstraction layer.

---

### Post by TpwUK on 2011-02-18
Wow - sensitive bunch aint ya

Every database has a structure - Every database starts as a set of rules, i.e 

this field has this type of data of whatever size

and every database starts with 0 records.

Programmatically the developer would create the structure of the record and apply whatever size rules/restraints are required, and then call something like ThisDatabase->Open(dbFileName) if the file dont exist then create the file.

You are now at a position where you can start adding data to fill a record, but otherwise all you have is a blank database file regardless of its format even MySQL uses BDB for it's own management internally.

Stop trying to torch me - open your minds - I can program the structure manually its just a tedious job, all i was after was a simple front end to do the dirty work. I don't need it to do anything other than just that. Any data manipulation (transactions) there-after is down to me and how I interface with BDB API's to get the results needed.

TpwUK

---

### Post by thornmastr on 2011-02-18
Wait. Desist. Calm down. Take a step backwards. Honestly, no reply you have received has torched you. One was a bit impatient but I truly think he/she was trying to get you to see that you might be making too much out of your file manipulations. 

One of the delights of programming is that it gives the programmer the chance to learn and to grow. By all means, pick a solution and fly with it. In this profession, the right way is never the 'only right way'. What I, and what almost everyone whom you may encounter here and in the profession would ask, is that you open your mind to different possibilities and different methodologies and that you try more than one. 

Hopefully, I have sparked a small interest in SQLlite and if you choose not to use it on this project at least you will know of it for the next project or the next.

HTH,

Thorny

---

### Post by Bodsda on 2011-02-18
Let me start by saying I have no idea about what Berkely DB is, but I do work with databases. If I wanted a key value pair list, I immediately think of a db with one table and two columns, named "key" and "value"

The ammount of time you have wasted complaining on this thread, you could have fired up MySql and created this db ages ago.

Alternatively, if your application is simple enough, why not just go with a bog standard text file that has "key,value:key,value:key,value" etc. Or perhaps even an xml file. 

This is a programming sub-forum, you asked a technical question and seem surprised when people give you a programatical solution. Work out what you need before you decide what you think you what

Bodsda

---

### Post by TpwUK on 2011-02-18
Hello again, thornmastr - I am just getting frustrated with it all ... I know what i want to do. I appreciate that there are alternatives even down to just using a simple text file (BodSda), or even a CSL etc.

I love the ideas behind SQL and the freedom that this offers to a huge database management and administration schema, but I then see it as my simple app would now need a server/database engine, an administrator an sql expert at hand to offer user support etc, when in reality this project is just meant for a single user within a single PC environment so forgive my ignorance levels if i say that SQL is overkill for what i want to achieve.

All i need is a simple Data store solution and the only match i could find for that was Berkely DB and it was the closest match i could find to the old Delphi & C++ Builder Database Express components. But since i cant even get any sample of BDB to play its looking like i need to read even more, and mess around with where bits and bobs have been placed.

I love Linux but it really does need to get its file structures sorted out

As BodSda has said, the amount of time i have spent looking for a solution could have been spent just typing it all in anyway ;) i wouldn't mind so much but all that typing still to do and i still cant even get Db db(NULL,0) to compile so i guess its back to the books

TpwUK

---

### Post by Some Penguin on 2011-02-18
> **TpwUK said:**
> Wow - sensitive bunch aint ya

Every database has a structure - Every database starts as a set of rules, i.e 

this field has this type of data of whatever size

and every database starts with 0 records.

Berkeley DB does not have record structures. 

> 
You are now at a position where you can start adding data to fill a record, but otherwise all you have is a blank database file regardless of its format even MySQL uses BDB for it's own management internally.

You are *deeply* confused.

---

### Post by TpwUK on 2011-02-18
Hi Penguin, thanks for the reply

>  Berkeley DB does not have record structures. Technically true ... But for trying to make things easier for other people to understand I used the terms tables, structures and records 

> I&#8217;ll go over some terminology used in
Berkeley DB. What is normally referred to as a table in most database systems is called a database
in Berkeley DB, and what is referred to as a database in other databases is called a database
environment in Berkeley DBThats a quote from * The Berkeley DB Book * -  Himanshu Yadava


> You are *deeply* confused. 

Please feel free to elaborate - My terminology may not be totally accurate but its clearer than an ambiguous statement like that

TpwUK

---

### Post by lisati on 2011-02-18
> **thornmastr said:**
> 
One of the delights of programming is that it gives the programmer the chance to learn and to grow. By all means, pick a solution and fly with it. In this profession, the right way is never the 'only right way'. 
I like this thought. On the rare occasion I do any programming these days, I sometimes find my thinking influenced by the fixed length record layout imposed when I was first learning programming - in those days the use of punched cards with their 80-byte records was a lot more prevelant than it is these days. It can be a bit of a stretch to adapt to other ways of doing things.

When I first saw this thread, before there were as many replies, I wondered if the OP read the word "SQLite", saw the "SQL" part, and was discouraged in some fashion.

Good luck on your adventures!

---

### Post by Some Penguin on 2011-02-18
For instance, MySQL has ca. nine possible database engines (last I checked, which was months ago; hopefully, MyISAM has been abandoned...), each of which may have its own storage formats.  InnoDB has its own [http://forge.mysql.com/wiki/MySQL_Internals_InnoDB]("http://forge.mysql.com/wiki/MySQL_Internals_InnoDB") structures.   Aria has its own file formats.  MyISAM had its own formats.  And so forth.

The physical organization including page format is *quite* important to RDBMS performance (and reliability...), was and presumably is still an area of active research, and is not something that is often delegated to a generic K/V store, be it BDB/DBM, [Kyoto|Tokyo] [Cabinet|Tyrant], MongoDB, or the like.

The simplest you'll get w/ a DBM-esque (BDB, Kyoto, etc) KV store + JSON for serialization.  It won't let you efficiently query by specific fields, but that's not what KV stores are for; if you want that, then use an RDBMS.

---

### Post by Bodsda on 2011-02-18
> **TpwUK said:**
> Hello again, thornmastr - I am just getting frustrated with it all ... I know what i want to do. I appreciate that there are alternatives even down to just using a simple text file (BodSda), or even a CSL etc.

I love the ideas behind SQL and the freedom that this offers to a huge database management and administration schema, but I then see it as my simple app would now need a server/database engine, an administrator an sql expert at hand to offer user support etc, when in reality this project is just meant for a single user within a single PC environment so forgive my ignorance levels if i say that SQL is overkill for what i want to achieve.

All i need is a simple Data store solution and the only match i could find for that was Berkely DB and it was the closest match i could find to the old Delphi & C++ Builder Database Express components. But since i cant even get any sample of BDB to play its looking like i need to read even more, and mess around with where bits and bobs have been placed.

I love Linux but it really does need to get its file structures sorted out

As BodSda has said, the amount of time i have spent looking for a solution could have been spent just typing it all in anyway ;) i wouldn't mind so much but all that typing still to do and i still cant even get Db db(NULL,0) to compile so i guess its back to the books

TpwUK

I think you are over complicating the matter - you don't need a SQL DBA, a server, or any support for the underlying systems, that's your job, as the programmer to male sure they work. Take a guess at how firefox stores bookmark and history information on a windows machine, its an a sqlite database. A single file buried deep in the application directory. Its not complicated, its not complex, it doesn't need a dedicated server... And I have never had to call Mozilla SQL tech support have you? I would imagine that on Linux it uses the same approach, but I can't confirm that at the moment,

If all you need is somewhere to store a few bits of data, stop complicating things and just whack them in a text file, write a short function for grabbing the key/value pairs and put them into an array, eliminate the database altogether. 

If field size/type constraints are a must, then perhaps look into doing the check at the input level

Why not post your code so we can have a look and recommend some suggestions. You really haven't given us much to go on so far.

Just my 2 pence

Bodsda

EDIT: oh, and if by file structure you mean file system structure. Take one look at how Win7 is handling the users area (Previously "documents and settings") - then feel free to come back and retract that statement :)

---

### Post by PaulM1985 on 2011-02-18
Stick it all in a comma separated text file. :p

Paul

---

### Post by TpwUK on 2011-02-18
> I think you are over complicating the matter - you don't need a SQL DBA,  a server, or any support for the underlying systems, that's your job,  as the programmer to male sure they work. Take a guess at how firefox  stores bookmark and history information on a windows machine, its an a  sqlite database. A single file buried deep in the application directory.  Its not complicated, its not complex, it doesn't need a dedicated  server... And I have never had to call Mozilla SQL tech support have  you? I would imagine that on Linux it uses the same approach, but I  can't confirm that at the moment,

I think you may have something there ... The more i read the more i seem to think i have to avoid or adopt!

>  If all you need is somewhere to store a few bits of data, stop  complicating things and just whack them in a text file, write a short  function for grabbing the key/value pairs and put them into an array,  eliminate the database altogether. 

It has certainly crossed my mind, but if i make references to files that move then i have a lot of problems.

>  If field size/type constraints are a must, then perhaps look into doing the check at the input level

Yeah i was already going to put in input checking for compliance

>  Why not post your code so we can have a look and recommend some suggestions. You really haven't given us much to go on so far.

I would if i had some to let you see, as i said earlier i cant even get Db db(NULL,0) to compile, i have discovered that the error is to do with a link library that's not in the right place, but i fix that, and i now get exception.h as a file not found and i have 6 to choose from but none where i expected, hence my file structure statement.

>  EDIT: oh, and if by file structure you mean file system structure. Take  one look at how Win7 is handling the users area (Previously "documents  and settings") - then feel free to come back and retract that statement :smile: 	

I gave up with windoze with vista reverted back to xp for the mrs, and have a ubuntu dual boot instead. Its a difficult transition with some things but with others its a doddle

Many thanks for the comments though Bodsda :P

TpwUK

---

### Post by bouncingwilf on 2011-02-18
Just for clarity - sqlite databases are just text files! as the documentation explains, just consider the sqlite engine as a replacement for fopen,fread...etc. I use them extensively and find them small, fast and efficient (for modest jobs anyway)

Bouncingwilf

---

### Post by TpwUK on 2011-02-18
Ok, the database i have in mind for contact/suppliers is really straight forward and simple

Record ID (used to identify a specific supplier)
company details - name address, country, telephone number, URL etc
contact within that company and there e-mail and location
company logo to be printed by the main app in a pdf catalogue

the only thing that needs looking up from this database is the company name hence there is no real need to SQL - If the company name is not in the DB then the main application calls the DB Editor screen for the user to provide the details of the new supplier.

all this started because i asked if there was a simple GUI app that would speed things up by creating the field names, what type they were, their max size and to just save it out as a blank *db that i could then access using the Berkeley DB C++ API

TpwUK

---

### Post by thornmastr on 2011-02-18
> **lisati said:**
>  On the rare occasion I do any programming these days, I sometimes find my thinking influenced by the fixed length record layout imposed when I was first learning programming - in those days the use of punched cards with their 80-byte records was a lot more prevelant than it is these days. It can be a bit of a stretch to adapt to other ways of doing things.

Good luck on your adventures!

Wow, another person from the days of Knuth and Ellison. 

While you may from time to time work with the 80 byte format; I well remember the shiny steel of the deadly sorting needle and the 029 (I think) Sorter. And gasp, programming with cables, blue black and red. Rats, I'll never see 20 again.

Thanks for some great memories of bygone times.

Thorny:D

---

