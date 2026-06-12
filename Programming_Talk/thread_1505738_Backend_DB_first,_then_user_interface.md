---
title: "Backend DB first, then user interface?"
date: 2010-06-09
forum: Programming Talk
---

### Post by memilanuk on 2010-06-09
Hello,

I've been tinkering away, learning a bit of php, mysql and python from books and tutorials, kind of alternating between the two depending on the week ;)

I have a program I'd like to create, and most likely its going to rely heavily on a database backend.  I'm still waffling a bit whether to pursue making the app something from a web browser with php/mysql, or python/some-gui-api/mysql.  Just for the experience, I've contemplated implementing it both ways just to see the differences.

I was thinking it might be prudent to get the database back-end sorted out first, tables all created and relationships established, and figure out the queries necessary for retrieving and updating various tables, etc. and then once that foundation is up and working, start working on the gui front end and application logic.

Is this a reasonably sound approach?  Anything wrong with doing the database-backend first?

TIA,

Monte

---

### Post by Barrucadu on 2010-06-09
That's usually how I do it; I just think of what I need to be able to store, and what I want to do with that, and then thinking of the table structure and relationships is very easy. Once that's done, I'll start building the system itself.

---

### Post by DanielWaterworth on 2010-06-09
I'd recommend starting with the DB first. I'd also recommend using Django. It's a web-framework for writing web-applications in Python. One of it's best features is it's ORM (Object Relational Model), basically, you write you're database schema as Python classes and then you can interact with your database by manipulating Python objects. On top of that you then get an admin interface for your objects for next to no work.

---

### Post by Compyx on 2010-06-09
I would also recommend designing the database first, once the database back-end is set up properly, the front-end tends to write itself since the database design dictates the design of the front-end. A front-end with PHP/Ajax can be quite interactive, and since anyone with a browser can use the database interface without installing any additional software/libraries, you keep the burden on the end-user small.

An interface in Python should also be relatively easy to set up, Python has an excellent and very extensive standard library, and even a native GUI toolkit (Tk) which again requires no additional setup. Although I personally don't like Tk, I'd go with Gtk+.

---

### Post by memilanuk on 2010-06-09
I've seen mention of Django a few places, citing that it would be good for creating web apps with python and all... but I'm not sure yet exactly how I want to run with this project.

The kicker is that it is something that should be able to be handed off to end users (match directors and score keepers for a particular flavor of amateur sports) who may have wildly varying computer literacy levels.  If I can have a standalone packaged app written in python using sqlite for the backend database, with a gui front end that'd be great - except there is a possibility of needing to be able to connect to a network database server at a larger match so multiple people can do the data-entry grunt work.  As such, a web-based interface would be handy... and I could probably hand them a folder of scripts and an XAMPP install and that would work just fine.  From what I've read though, adding python/django to XAMPP is non-trivial.

As you can see... there are still a lot of 'ifs', and I'm trying to figure out which way is a better compromise of work/learning curve for me vs. for the end user - while I'm still learning to do this stuff in the first place.  Definitely makes me feel like I'm getting the cart before the horse at times.

Thanks all for the input,

Monte

---

### Post by McRat on 2010-06-09
...

---

### Post by Roptaty on 2010-06-09
> **memilanuk said:**
> Hello,

I was thinking it might be prudent to get the database back-end sorted out first, tables all created and relationships established, and figure out the queries necessary for retrieving and updating various tables, etc. and then once that foundation is up and working, start working on the gui front end and application logic.



I think I would have started with writing user stories first. Especially setting the requirements of the solution. 
Doing some mockups before you start, would also give some value and give some directions of what you need. 

Developing as a web application vs standalone application: 
You question the level of competence of the end user; Would the end user be able to install the xampp setup, and more importantly to setup the network, if needed? How open should the system be? Could the user use Web Hosting services? 


If multiple users are going to use the application; the easiest choice would be to have this as a web application. There you could use for instance django/joomla (cms)/cakephp or other frameworks. The good thing about using one of these frameworks is that you dont have to consider which database engine you are running on. The ORM does that for you. :) 

 
Standalone application:
Some people mentioned tk as gui. Even though an application may be functional as hell, I would hate using the an application written in TK, due to the uglyness. (my five cents).

I would use GTK/QT for the GUI.

Standalone application talking to a database server:
This adds more complexity to the task. You have to think about:
- version control of the applications vs the database model
- where to put the business logic

Advanced solution:
One way would be to put all the business logic into an application server that your application talks to through SOAP or other means. The application server handles all the communication to the database. This way, you only have to change the application server, instead of making sure that all the clients are running the correct version. (You still have to do this, but now the application server may deny access if the version is incorrect).




My ten cents for this application:
I think I would have approached this as a web application, since this will allow multiple people to insert results/matches (and even see statistics).

---

### Post by memilanuk on 2010-06-09
Therein lies the rub.  Currently most of the people that take care of these functions at events are using older laptops or PCs running either a) spreadsheets they've thrown together or b) ancient (and cranky) software written in BASIC in a DOS box(with an interface that makes ncurses or tkinter look beautiful) and won't even run on Win Vista/7.  The primary redeeming features of the DOS program over the ad-hoc spreadsheets is that it has some purpose-built functions, such as squadding and seeding and printing labels and match bulletins.

99% of the time the user is going to be running solo - one person, one computer, no network.  The actual functions - entering competitors into the program, squadding them in relays, seeding them based on performance for the next day, and sorting the results based on league rules is way more important than network access of any kind.  Printing the results neatly to a PDF file (there are the results the competitors want to see, and then there are the results that the sanctioning body wants to see) is probably more important that network access.  Competitors would not in any situation be connecting to the application to view results - it is strictly a data entry and match administration tool.

It's that 1% of  the time, at a larger event (regional or above) that *might* have enough volunteer help that having network access would be desired.  What I envisioned was *one* person that is semi-competent to set up their computer as needed, and the rest can connect via wifi/LAN (how they do that is their problem, not mine) to a web page so there can be multiple people working on it.  There are really only two times that multiple people are desirable or even necessary - during sign-in, when folks line up to get registered, and then when scores are coming in and there is a certain amount of pressure to get them entered and tallied so the awards ceremony can get under way - and done, so people can start the drive home.  

In that sense... the 'muli-user' interface wouldn't need to be near as full-featured as the master interface... just enough for data-entry.  The actual complicated part of setting up the tournament and dealing with the results would ideally be done by one person, sitting at one computer.

Distributing the application to the users is the other big headache/nightmare.  The vast majority are going to be using Windows or possibly a Mac, probably on older hardware that is at least a couple generations (minimum) behind the curve.  Honestly what I'd been kicking around in my head the most was a php/mysql app that could be (primarily) dropped into the htdocs folder of an XAMPP install (XAMPP seems to be pretty simple to install on Windows, Mac, or Linux), and once they fire up the Apache/MySQL server and navigate to the home page, it would run a script to set up the database tables and pre-populate them with default data and present them with a relatively familiar browser-based interface.  Problems include printing (pagination) and all the assorted un-necessary crap that some XAMPP installs include with them (Tomcat, Mercury, etc.).  A stand-alone python/tkinter-or-wxpython/sqlite application seems like it would be *far* easier to distribute, but that 1% network usage becomes the problem.

FWIW, I *am* an end-user, so I'm more than passingly familiar with the available solutions out there, such as they are, and its primarily my frustration level with them that has me wanting to dig in and make something, anything, that is better than what we have now - even if it is way above my current ability.

---

### Post by soltanis on 2010-06-09
Just my 2 cents, but I hate databases, especially the relational kinds.

---

