---
title: "Programmer wanted for database project"
date: 2008-08-26
forum: Programming Talk
---

### Post by MadsRH on 2008-08-26
Hi
_This is NOT a paid job!_

I'm a music teacher and I'm seeking help (a programmer) to create a program to keep track of what I have taught during my lessons and the like.
With around 45 pupils per week can be very difficult to remember who has done what. So I would like to have a program with a kind of database of students' data + my own notes for each session.

There are five permanent data per. student:
-- Name (*Thomas Larsen*)
-- Address (*Gyvelvej 15, 9400 Nørresundby*)
-- No phone (*86425465*)
-- Instrument (*Guitar*)
-- Teaching time (*15:30*)

And three per data. lesson:
-- Attendance (*Showed up*)
-- Lesson summary / description (*We played some guitar rock...*)
-- Date (*3/4-08*)

Such a program will certainly be useful for many teachers - and not only music teacher. Of course the project should be open source so others can contribute and further develop the program.

I am not sure which language program to be written in, but I imagine it should be multi-platform and then Python probably would be a good bid or what? I have made a (windows) mockup of the program:
[ATTACH]82862[/ATTACH]

This is the first draft of the program, but I hope in the future in will include other features like: Making schedules, Attendance statics, band or ensemble lessons...
I have no programming skills, so I'm really looking for a person/persons who wants to take on this project. I will be able to help with graphics, website and the like.

Looking forward to reading your reply.

**//MadsRH  **
madsrh(a)gmail.com

PS: If you have comments like "this is a stupid project", please post them in a constructive way too ;-)

---

### Post by harrysales on 2008-08-26
Hello There,

I would do this as a php mysql combo.
In your db you look as if you require two tables.
One for the Students and One for the lessons.

tblStudents would be.
col 1   Id (a unique idnetifier for the record)
col 2   Student Name
col 3   Other student detail
col 4   Aniother stdent detail

tblLesson would be
col 1 Id (a unique idnetifier for the record)
col 2 StudentId (to indicate which student record is attcached to)
col 3 LessonDetail
col 4 another lesson detail

You would require the following to 
1 page to add students
1.5 page to select student record for editing.
2 page to edit students
3 page to add lessons
3.5 page to select lesson record for editing
4 page to edit lessons

Once this basic set up is in place you can expand it without limits

You would need to install apache, php and mysql on to your box.

can you do any of it?

Harry

---

### Post by mihalisla on 2008-08-26
I 'm trying to make a relational draft of what u said!
Could you tell me if one lesson could be formed by more than one students?
We have to make and normalize the base first!

---

### Post by henchman on 2008-08-26
You could code the site so that any music teacher can register and use that site for managing his courses :popcorn:

edit:
i don't want to take your fun away, but may be [http://www.musicteachershelper.com](http://www.musicteachershelper.com) just what you like xD

edit:
just saw that it costs money... you have decide for yourself if 25 bucks are worth it or not..

---

### Post by pmasiar on 2008-08-26
... or try to someone with basic Python skills and looking for a project to tackle. This looks like quite simple application in Google App Engine with Django.

---

### Post by Mickeysofine1972 on 2008-08-26
Hi

I think i get your idea and would be interested in doing this for you.

Can I  ask a few more things though:

- how do you want reports of the info? (do you want to see pages of info or just a report on a person by person basis?)

It seems that whilst you have a good start in how to get the info input, you will need at a later time to be able to ask queries like "what has john smith done so far?" so how would you picture that?

Mike

---

### Post by MadsRH on 2008-08-26
Hi everybody. Thanks for all your replys.

_Harry_ -> I'm not sure I understand everything in your post. I don't know much about programming, so for me a php mysql combo sounds good, but it has to work offline! Anyway, it sounds multi-platformish.

_Mihalisla_ -> If I understand you correctly, your asking if the lesson could include more people, like in bands or ensembles. If that's your question, than no not a the time, but it would be great.

_Henchman_ -> Thanks for the info, Ill check it out. Perhaps we can get some inspiration there.

_Mickeysofine1972_ -> It would be great if you would help out (Actually I saw your name in another Programmer help wanted post ;-)).
My first thought on how the reports should be viewed was simply to browse though the data via the UI (using the up/down date buttons and the *next/previous student* buttons).
But we will have to do some thinking as to what would be the most useful way.

- 

What's the next step? What can I do to kickstart this project? Should I set up at Launchpad site? If any of you have started programming, please share it, so we don't have four projects of a kind in four different languages.

Again, I want to thank you all for showing your interest. I really hope this project takes off.

**//MadsRH**
madsrh(a)gmail.com

---

### Post by CptPicard on 2008-08-26
Python + SQLite + some GUI toolkit of choice. :) I honestly don't understand where these web app suggestions are coming from.

---

### Post by mike_g on 2008-08-26
What about M$ Access, or whatever the open source equivalent would be? IMO that would probably be the easiest method. If you want to code it your self then the interface is going to be most of the work. I would do what CptPicard said and use SQLite; you shouldent have to install and run a MySQL service just so you can use a simple little db app.

---

### Post by CptPicard on 2008-08-26
> **mike_g said:**
> What about M$ Access, or whatever the open source equivalent would be?

Oh... OO Base is worth looking into. +1

---

### Post by tbunix on 2008-08-26
I agree. Open Office database is ideal for a personal non-programmer small project.

You won't have to deal with learning database administration or a general pupose programming language or a GUI toolkit. The wizards will walk you through most of what you need.

the first step is to layout the tables and relationships

Do you ever have more than one student in the same lesson? if yes do you consider that two separate lessons? 

are all lessons the same length? for billing purposes?

do lessons have types beyond instrument. e.g. beginner, intermediate: playing skill, music theory - do you care?

I don't under the address. is 15 an apartment number and 9400 a street address? do you need town and zip code? email address? emergency contact?(name work TelNo, Cell TelNo?
Date Of Birth? 


do you want/need a scheduling calendar?
an invoice tracker?

these can be added later

---

### Post by Mickeysofine1972 on 2008-08-27
> **CptPicard said:**
> Python + SQLite + some GUI toolkit of choice. :) I honestly don't understand where these web app suggestions are coming from.

I agree Python + SQLite is a good choice, I also prefer wxPython as the GUI tool kit as it easy to make with wxGlade.

Ok I will start something tonight after work :)

Mike

---

### Post by MadsRH on 2008-08-27
> **tbunix said:**
> I agree. Open Office database is ideal for a personal non-programmer small project.

You won't have to deal with learning database administration or a general pupose programming language or a GUI toolkit. The wizards will walk you through most of what you need.

the first step is to layout the tables and relationships

Do you ever have more than one student in the same lesson? if yes do you consider that two separate lessons? 

are all lessons the same length? for billing purposes?

do lessons have types beyond instrument. e.g. beginner, intermediate: playing skill, music theory - do you care?

I don't under the address. is 15 an apartment number and 9400 a street address? do you need town and zip code? email address? emergency contact?(name work TelNo, Cell TelNo?
Date Of Birth? 

do you want/need a scheduling calendar?
an invoice tracker?

these can be added later

I can't really take in how to layout the tables and relationships :confused:

I thought that a lesson with more than one student would be difficult to program (I can't keep track of what goes where in the database!), but maybe it would be easiest be incorporate that "feature" from the beginning.
In lessons where I have more than one student (a band or ensemble) I will need name, addresses and contact info for each student (that could be anything from 2 to 12 students in the same lesson). There would be only one lesson description or text box for the entire band - that should be sufficient. 

Not all lessons are the same length. There should also be a way to choose witch weeks there is holidays and so one.
The type of lesson (e.g. beginner, intermediate: playing skill, music theory) would be info I would add in the lesson description text box.

In the mockup I've written street (Gyvelvej), apartment number (15), zip code (9400) and town (Nørresundby) in the same line, witch properly should be separated. More data fields could be added, like: mobile phone, email...

I don't _need_ a scheduling calendar, but it would be a nice feature :)
I also think that there should be a way to add a lunchbreak.

**//MadsRH**

---

### Post by MadsRH on 2008-08-27
> **Mickeysofine1972 said:**
> I agree Python + SQLite is a good choice, I also prefer wxPython as the GUI tool kit as it easy to make with wxGlade.

Ok I will start something tonight after work :)

Mike
Sounds great Mike :)


Have you guys got any suggestions for a name for the application???

My first thoughts are:
- Lesson Log
- Lesson Manager
- KeepTracker
- Overview
[B]
//MadsRH[/B]

---

### Post by Mickeysofine1972 on 2008-08-28
How about the Tonic Music Manager? hehe!

I started building the interface and I'm almost ready to start putting in the code.

I'll be back when the code is starting to develop into something you can play with.

Mike

---

### Post by Griff on 2008-08-28
I'll have to second the php/mysql idea.  The interface would be handled through a browser (no, it won't require internet) so finding someone with some html skills should be easy.  Php is a scripting language you embed in html and in this case would be responsible for communicating back and forth with the database.  Php is oss and employed in all environments.  MySQL is also oss and employed in all environments.  Both are stable and reliable.  MySQL tables are also very easily backed up and simple to restore. Example:
Backing everything up:
```

$ mysqldump -u root -p --all-databases > db_backup.sql

```
Restoring it all:
```

$ mysql -u root -p < db_backup.sql

```

---

### Post by Mickeysofine1972 on 2008-08-30
Ok i've started ,(finally! I got side tracked with a major problem with a clients webserver, but I'm back on track), to build the database.

In your screen shot, what does the '3/4-08' mean? so I can give it a name in the database table.

Mike

---

### Post by Mickeysofine1972 on 2008-08-30
> **Griff said:**
> I'll have to second the php/mysql idea.  The interface would be handled through a browser (no, it won't require internet) so finding someone with some html skills should be easy.  Php is a scripting language you embed in html and in this case would be responsible for communicating back and forth with the database.  Php is oss and employed in all environments.  MySQL is also oss and employed in all environments.  Both are stable and reliable.  MySQL tables are also very easily backed up and simple to restore. Example:
Backing everything up:
```

$ mysqldump -u root -p --all-databases > db_backup.sql

```Restoring it all:
```

$ mysql -u root -p < db_backup.sql

```

Actually, your right that PHP/MySql are a great choice for this sort of thing, but it actually turns out that doing this in Python and sqlite isn't that much different :D

I learned PHP and Mysql before I learned Python and I have been pleasantly supprised that developing GUIs isn't such a difference experience using Python.

The real difference is when you come to install it on the users computer. unless you install a webserver like apache on the machine then PHP isnt a good option, but with py2exe you can turn your Python apps into a exe and just copy the needed file to the computer then run it.

The really cool thing is that the Python stuff can be run the same way on Linux, Windows and MAC! so you write it once and run it anywhere, and most importantly you dont have to install Mysql and Apache

Mike

---

### Post by MadsRH on 2008-08-30
The '3/4-08' is the lesson date. I'm not sure if a calender option would make it easier to keep track.

Perhaps the contact info (except the name) should be hidden, so I you needed to contact the student your could click the **>>** (expand info) icon next to the text.

Mike, if you have questions you can also contact me by email at madsrh(a)gmail.com - just in case I miss you post here in this thread :)
[B]
//MadsRH[/B]

---

### Post by Mickeysofine1972 on 2008-09-14
Ok I have been working for a while and it looks as though I'm not gonna be able to finish this on my own.

So here is the code so far for anyone who is interested to get involved

Mike

---

### Post by SteelDragon on 2008-09-14
I'm quite green when it comes to programming and database management, so I don't have anything of substance to contribute, I just wanted to mention I like the idea and I'll be following along.

This is particularly interesting to me as I started just this week on a small project using SQLite and python, and was planning to get into wxPython this week. Lucky coincidence for me as I don't really know what I'm doing so hopefully I can learn something by watching this thread.:)

Good luck to everyone involved.

---

### Post by SteelDragon on 2008-09-28
This is disappointing. Did anything ever end up happening here?

---

### Post by Mickeysofine1972 on 2008-09-29
I was hoping that some of the other Python gurus on the forum might get involved as I got a s far as I had time to myself.

The program is about 50% done really if some of the others would like to contribute then this could be finished pretty soon.

Mike

---

### Post by mike_g on 2008-09-29
I could maybe pick this up if the OP is still around as I made a little pygtk/sqlite address book program. So it would just involve adding an extra table plus a dialog for the classes.

---

### Post by Mickeysofine1972 on 2008-09-29
That would be great!

I knew someone from this excellent community would step to the task!

There is already a database module in there you can add to as a beginning if you need any help I can answer any questions you might have. 

Sorry I cant help any more than that but I dont have time to do any coding you see.

Mike

---

### Post by mike_g on 2008-09-30
I have a working version now. I did it in pygtk as thats what I was working with before (sorry mikey). Theres a screenie  [Here](http://i92.photobucket.com/albums/l15/mikegrundel/2008-10-01-005848_1024x768_scrot.png).  The main window is basically two list views. The lefthand list allows for selecting a student and the right hand list displays all the classes that the student has taken/booked. The only thing I havent got around to yet is the view dialog for classes (but you can see all the details by clicking edit anyway). Any bugs or suggestions; let me know. Cheers.

---

### Post by Mickeysofine1972 on 2008-10-01
> **mike_g said:**
> (sorry mikey) 

Nothing to be sorry about! thats a good bit of coding, well done mate! keep up th egood work.:D

Mike

EDIT:

Actually, this looks like it would have been easier to write using pygtk, I think i will investigate further if I ever get a moments peace :S

---

### Post by mike_g on 2008-10-01
Yeah, pygtk is nice to work with. But then its probably easier for me as I have used Gtk in the past as opposed to wxWidgets. 

If you (or anyone else) like you could have a go at making a view class dialog with it for the program. It would be a fairly easy place to start. Glade can pump out the interface XML for it and view_student() function and ViewDialog class contain the sort of code you required to display it. Just an idea in case anyone wants to add something to it.

---

### Post by MadsRH on 2008-10-01
I've set up a Launchpad account under the name Syllabus
[https://launchpad.net/syllabus]("https://launchpad.net/syllabus")

I haven't uploaded any code simply because I don't know how :confused:
[B]
//MadsRH[/B]

---

### Post by dje on 2008-10-01
> **MadsRH said:**
> I've set up a Launchpad account under the name Syllabus
[https://launchpad.net/syllabus]("https://launchpad.net/syllabus")

I haven't uploaded any code simply because I don't know how :confused:
[B]
//MadsRH[/B]

there is a nice howto in [URL="http://fullcirclemagazine.org/issue-4/"]issue 4 of full circle magazine
[/URL]
hope that helps
dje

---

### Post by MadsRH on 2008-10-02
Thanks :D

---

### Post by MadsRH on 2008-10-23
I really can't figure out Launchpad (would probably make more sense if I was an actual programmer), so I  don't know how to upload files and by now I've given up. If you want to help out with this project (submitting code or just help uploading files) you can join the team: 

_**Team:**_
[https://launchpad.net/~syllabus]("https://launchpad.net/~syllabus")

_**Project:**_
[https://launchpad.net/syllabus]("https://launchpad.net/syllabus")



[B]
//MadsRH[/B]

---

### Post by Rich78 on 2008-10-23
For something as small as this, I don't know why you didn't just use a spreadsheet?

Tab (worksheet) per student and then just log the data in date order?

It seems bit like using a mallet to crack an egg.

---

### Post by DrMega on 2008-10-23
> **harrysales said:**
> Hello There,

I would do this as a php mysql combo.
In your db you look as if you require two tables.
One for the Students and One for the lessons.

There are three tables if the data is to be fully normalised and efficient.

You need a 'student' table and a 'lesson'. Obviously the student details go into 'student' and the lesson date, content, summary etc goes into 'lesson'. Then you need an 'attendance' table. This would have foreign keys to both 'student' and 'lesson'. That way, the 'student' table remains fairly static. The 'lesson' table is populated in advance of lessons (or just after), but only one row per lesson, and the 'attendance' table just holds links linking student records to attendance records, so you can say *student x* attended *lesson y*.

---

