---
title: "Linux at Home/ Xp at work, need Db on a thumb drive in the middle."
date: 2009-03-23
forum: Programming Talk
---

### Post by Jonas thomas on 2009-03-23
I posted something similar in the water cooler sub-forum and so far no responses.

I've been really getting into GTD (David Allens Getting things done) and I like to be able to but my list of things/projects in a database on a thumb drive and run it either in at work or at home.

It would probably be painless for me at work if I did this in access.  I could either generate a query or build a VB front end to get what I want.

For home I was thinking about unixODBC, MDBtools.  But from what I'm reading data more or less flows from out of Access using MDBtools but not no so good on inserting data into an MDB. One of these features under development deals. (Does anyone know how far along this feature is??)

Basically, my needs are some what simple, a project table and an action item table linked to a project_ID.

I'm not locked into access, but I thought it would be easiest for me at work since I have the tools at hand. Any suggestions/thoughts would be appreciated.

Thanks,
JT

---

### Post by stevescripts on 2009-03-23
SQLITE - the same db will run on both platforms - 

[http://www.sqlite.org/](http://www.sqlite.org/)

Hope this helps a bit.

Steve

---

### Post by cknoblock on 2009-03-23
I would try openoffice.org's Base program.  It has a similar design to Access and save the data file as an ODB.  Then you can open it in openoffice on either computer.

---

### Post by Jonas thomas on 2009-03-23
> **cknoblock said:**
> I would try openoffice.org's Base program.  It has a similar design to Access and save the data file as an ODB.  Then you can open it in openoffice on either computer.
That would be the easiest solution.  I need to float that concept with my IT department at work and see what they think....
Thanks....

---

### Post by indylarry on 2009-03-23
Have you considered [GTDTiddlyWiki]("http://checkettsweb.com/tw/gtd_tiddlywiki.htm")? It runs in the browser so you don't need to install anything.

---

### Post by Jonas thomas on 2009-03-24
> **indylarry said:**
> Have you considered [GTDTiddlyWiki]("http://checkettsweb.com/tw/gtd_tiddlywiki.htm")? It runs in the browser so you don't need to install anything.

That is very interesting, Thanks and I think I might use this as reference.  I would prefer keeping my personal/work information on a thumb drive..

---

### Post by Jonas thomas on 2009-03-24
> **stevescripts said:**
> SQLITE - the same db will run on both platforms - 

[http://www.sqlite.org/](http://www.sqlite.org/)

Hope this helps a bit.

Steve

This path offers some potential to me.
I downloaded the ODDB driver and Open-Office base before work this morning from synaptic but haven't had a chance to play with it.

I was looking for a ODBC driver for sqlite for XP.  Silly question here.   Does sqlite.org provide ODBC drivers for use in windows?  I was poking around their site and haven't come up with anything yet.  I found sqlite drivers from sites other than sqlite, but the our IT department is rather sensitive about installing 3rd party stuff on their PC's (Rightly so I guess)

I would think I could use Access or Base depending on OS to start out with to access the db on the thumb drive.  THis should work right??
I suppose the more I get into it I could write a python front end. (Of course than I need to talking the IT department into letting me install python on my windows machine )  I wonder if I could have python installed on the thumb drive to run in windows without installing anything.  Hmmmmm.

---

### Post by Jonas thomas on 2009-03-24
> **indylarry said:**
> Have you considered [GTDTiddlyWiki]("http://checkettsweb.com/tw/gtd_tiddlywiki.htm")? It runs in the browser so you don't need to install anything.

I tried the link at home using Linux/Firefox.  Using XP and Explorer, it seems like it's not resizing properly.


[Edit] Duh... I went to [http://www.tiddlywiki.com/]("http://www.tiddlywiki.com/")  They say you can install it on a USB stick.. Hmmm... I need to look at this some more.  This looks like maybe it should be my plan "A"
Thanks,

---

### Post by stevescripts on 2009-03-24
Jonas - 

There certainly is a lot of 3rd party stuff available for SQLite, and I am not familiar with much of it.

I use the tcl interface to SQLite, as the SQLite author was for many years, a contributing member of the Tcl Core Team.

As an alternative to asking your IT folks to let you install python on your windows box - you can, using Tcl/tk - put both a linux tcl/tk executable, and a windows one, on the same usb drive, along with just one copy of the SQLite db, and just use the appropriate tclkit for whichever OS you have the drive plugged into at the time.

If you want more info, just google for tclkit - or see my website. ([http://www.stevescripts.com](http://www.stevescripts.com))

Feel free to contact me if you wish.

Steve

---

### Post by Jonas thomas on 2009-03-26
> **cknoblock said:**
> I would try openoffice.org's Base program.  It has a similar design to Access and save the data file as an ODB.  Then you can open it in openoffice on either computer.

Current my Gtd needs are pretty simple but they're evolving as I get further into the book.  My first attempt was a list that I was keeping in excel that had coding to sort by context.  I had project title, goal, next step in the same row.   Allen was talking about how you need to review your projects so I was thinking a logical next step to create to files with a project list and a actions list  linked through a project ID.

I've played with linking Excel to Access a couple of times and I think I even tried it doing a ODBC via dataenviroment in Vb6.  This was while back but and if recall it worked but not as sweet as access.  I need to do some experiments here....

But I'm thinking that maybe I could do my cross platform stuff via Excel using Access in XP and Base in Linux linked into the same Excel spreadsheet.  I'm pretty use I should be able to do some simple Sql joins, inserts and Deletes... Anyway that's the game plan to try..  
Has anyone been down this route??
JT
[Edit] I think this approach is a dead end.  It appears that OO.base queries allow read only access to a single sheet.  Darn it.  I thought I had something there.
[Edit again]
I tried to link a excel to Access.  I was able to get two tables to join in a query but as near as I can tell it's all read only.  So much for that approach.... Time for something else.

---

### Post by Jonas thomas on 2009-03-28
> **indylarry said:**
> Have you considered [GTDTiddlyWiki]("http://checkettsweb.com/tw/gtd_tiddlywiki.htm")? It runs in the browser so you don't need to install anything.

Ok... I downloaded the html file to my thumb drive my work and when I opened it up, was getting all kinds of warning from my browser that Java was trying to execute.. So... I decided to play with this thing at home.

When I got home I disconnected my internet connection and fired it up.
I have to admit that this thing is cool... Ability to store categorized notes within the HTML, A calender to store notes.
Although not exactly what I was looking for but it definately got my attention.

I've dappled a bit in PHP but I've never really played with Java..  So pardon my newbieish questions here: 

Apparently, this application will allow you to add notes and store it within the html file.  In general, how isolated is my computer/network from anything malicious that could potentially exist within Java code within the Html file? I'm not implying that there is anything bad in there, but there is a lot of truly impressive stuff going on this file.  (Our IT department keeps everyone on a leash, but mine fairly loose and long because I've never given them a reason to shorten/tighten it. I plan to keep it that way.) 

The thing that doesn't work is that I see no link of projects to individual tasks. (ala why I was looking for the relational data base).   

Currently, in my gtd'ification project. I get simple single step issues organized at work by the use of appropriate outlook folder.. Works well.

On my project stuff I have spreadsheet that I have Project, Project complete statement and next step in a row along with some context coding that I sort by.  I basically the file at work and print out report when I go home so I can cross things out or up. My system sort of breaks down when I have two next steps (I know that sounds silly) that can be applied in different contexts.

Gtd talks about how need to look at your projects and what defines complete by themselves. For myself, I'd probably like to outline my projects more like a gantt/pert chart.   I know that this sings relational database, but currently the IT department look warm about installing Sqlite ODBC on my computer (at the moment anyway) so I can go cross platform. (At this point, I'm not sure If I want to got the tcl/tk route.)

So here's the question. Is it possible to store relational data within a HTML (such as tiddlywiki) powered by JAVA?  For that matter, wouldn't it be possible to make something that resembles SQL??  It seems like this would be my best approach for addressing my pain here?? What do you guys thinks?  Maybe I need to add "Learn Java" on my list ;)

---

### Post by Jonas thomas on 2009-04-09
> **indylarry said:**
> Have you considered [GTDTiddlyWiki]("http://checkettsweb.com/tw/gtd_tiddlywiki.htm")? It runs in the browser so you don't need to install anything.

I just want to thank you, I did a little research on this and it seems that I'm going with tiddlywiki route route.  
I basically evaluated three tiddywiki's each customized for GTD and thought I'd share my 2c's in a mini software review

[gtdtw]("http://nathanbowers.com/gtdtw/")

[d-cubed]("http://www.dcubed.ca/Welcome_to_d-cubed.html") (aka d3)

[MonkeyGTD]("http://monkeygtd.tiddlyspot.com/#MonkeyGTD") (aka mgtd)

These applications are listed in sequence of technical sophistication.
For me the first (gtdtw) was a little too primitive and found mGTD too complicated for my taste. To me any d3 felt just about right.

The only thing negative I seen has been some complaints about slow response when you overload the file with too much data. (I'm still in the middle of populating d3 and I haven't noticed anything, my fingers are crossed).
As far as cross platform D3 is awesome.  I have it on a thumb drive and it works well in ubuntu/firefox as well as XP/IE(ver 7)
It did get weird on me when I first fired up in windows, with the sizing of the project text.  I resized the text in IE and all was well.
(I have someone with a mac coming in next week, who I might test this on)

The only D3 negative I've sound is that if you double click a tiddler instead of using the command boxes along the top of the tiddler, sometimes there are issues saving the changes.

Once again a thousands thanks with making me aware of this solution.

---

### Post by indylarry on 2009-04-09
I use it at work.  I am not particularly good at GTD, but I have really enjoyed having a place to empty my head that is not impeeded by my IT department.  You are welcome and I am glad to see you chose simplicity despite the urge to go the more technical route.  As linux users we would all rather be tinkering and customizing than getting things done.

---

### Post by Jonas thomas on 2009-04-09
> **indylarry said:**
> I use it at work.  I am not particularly good at GTD, but I have really enjoyed having a place to empty my head that is not impeeded by my IT department.  You are welcome and I am glad to see you chose simplicity despite the urge to go the more technical route.  As linux users we would all rather be tinkering and customizing than getting things done.

I'm really impressed by D3. There has been a huge amount of work befind this.  Assuming this thing is still usable once I get the thing fully populated. I'm going to steer a couple of schekels to some of it's creator's in gratitude... This stuff so far is awesome.. Hmmm... I guess I should add this to the list.. ;)

---

### Post by soltanis on 2009-04-09
Sounds to me like SQLite is the perfect solution for you (small, portable, cross-platform). If you know anything about Java you might be able to conjure up a little app that runs on both your computers and then use that to modify the DB, otherwise, tools exist that you can install on the computers at work and home to access/modify the database.

---

### Post by The Cog on 2009-04-09
If you use sqlite, you should be aware of a neat sqlite GUI too that is a add-on for firefox, called SQLite Manager.

---

### Post by Jonas thomas on 2009-04-09
> **The Cog said:**
> If you use sqlite, you should be aware of a neat sqlite GUI too that is a add-on for firefox, called SQLite Manager.

The only thing is that work uses IE and need to get IT involved to get sqlite running which is not a option at the moment.  Besides... so far d3 really meets my needs very nicely... But sooner or later I plan to do some Db stuff at home, this could be very useful..
Thanks,

---

