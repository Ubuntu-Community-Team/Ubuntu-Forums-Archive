---
title: "need help with alternative to Access databse"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by zippyties on 2008-08-26
I currently have a MS Access 2007 database.  The purpose of this database is to track construction prospects as they advance toward the bid phase.  I use it to keep track of my contacts and any documentation i receive.

Herein lies the problem; access has a database size limit @ 2gb which I am rapidly advancing towards.  This and Access is incredibly irritating and requires you to know visual basic if you want it to do anything other than make very basic reports.

I am a recent convert to Ubuntu and I love it!  However in order for me to make a full conversion I would need to have the above mentioned database, and I don't mind rebuilding it in another program, it isn't too complex.

If I am going to do a complete rebuild though, I would like to explore the possibilities of a server based DB that I can access from my computer @ work(Windows), and from my computer at home(Ubuntu).  Another reason is that as the department grows, there will be additional people working off of this DB.

What do I need in order to do this in Ubuntu?  I don't mind investing in a cheap server and opening a port in the firewall. Additionally i don't want to purchase a software license and then have to fork a thousand dollars a year just to have my somewhat simple DB.

---

### Post by Thelasko on 2008-08-26
You might not like my answer, but OpenOffice.org has a database application that's very similar to Access.  It might even be compatible.

---

### Post by jgrabham on 2008-08-26
> **zippyties said:**
> 
If I am going to do a complete rebuild though, I would like to explore the possibilities of a server based DB that I can access from my computer @ work(Windows), and from my computer at home(Ubuntu).  Another reason is that as the department grows, there will be additional people working off of this DB.

What do I need in order to do this in Ubuntu?  I don't mind investing in a cheap server and opening a port in the firewall. Additionally i don't want to purchase a software license and then have to fork a thousand dollars a year just to have my somewhat simple DB.

Using mysql would probably be the best option, look it up, there a probably different ways to set it up, but mysql is free (as in freedom AND beer).  Just read up on mysql, buy a book on it, or read about it online, and you'll be able to work out what you need to do.

---

### Post by zippyties on 2008-08-26
I had looked at Mysql, but it looks like you have to pay per year to use it.  Did I miss something there?

Thanks for all the quick help!

---

### Post by aloshbennett on 2008-08-26
MySql community edition is free to use. You have to pay for Enterprise edition. Using MySql Community edition, the only money you will have to shell out is for hosting your site.

---

### Post by Midahed on 2008-08-26
Either way, it will be difficult to avoid some sort of coding.  In my experience the OpenOffice Database is not as polished or as fast as Access.  I think it has a fair way to go before it reaches the standards set by Microsoft's offering.

Personally, I think you'll find it nigh-on impossible to produce what you want without having to get into coding at some level.  If you can overcome that barrier, you should be able to produce exactly what you want with a MySQL back-end whether you decide to front-end it with Access or the OpenOffice equivalent.

---

### Post by zippyties on 2008-08-26
Thanks for all the help guys!

in your opinion, on a scale of 1-10 for ease of use and quality of product, where would Mysql fall if access was at 5?

Also if learning some SQL is necessary what kind of difficulty factor/learning curve would i be looking at?  I don't plan on making a career of database programming, however it looks like some knowledge will be helpful in the future.

Thanks again!

---

### Post by OffAxis on 2008-08-26
What about kexi?
it's in the repos.

[http://www.kexi-project.org/](http://www.kexi-project.org/)

In regards to access...

Have you split your database Front end / backend?

Do you routinely 'Compact and Repair'?

If table size is really an issue you could have each table live in it's own database file and just combine them in the frontend by linking the tables.

Are you storing pictures in your database? I'm not quite getting how you approach 2GB worth of records...

---

### Post by drubin on 2008-08-26
> **OffAxis said:**
> Are you storing pictures in your database? I'm not quite getting how you approach 2GB worth of a records...

Agreed it is very hard to get a data base of size 2gigs with out images/mvoies.

Have you done any form of maintainance on the access data base.  ie compact and repair, I have noticed data bases go from 10mb to 400kb. (Not sure how this will affect yours though)

---

### Post by zippyties on 2008-08-26
For 6 months worth of records I have a 768 Mg database file.  The main reason I have this problem is because of embedded documents (plans, specs, news articles, etc).  I realize this is probably the most inefficient way to organize a database, however my database design abilities are extremely limited.  I tried linking to an existing location as opposed to embedding.  This didn't work as there are a few people who work with this database, and not all of them have access the the storage drive.

when it comes to linked databases I have had very limited results, here again my abilities are limited.

I don't mind learning a programing language if it will be worth the time and effort.

Thanks.

---

### Post by drubin on 2008-08-26
> **zippyties said:**
> For 6 months worth of records I have a 768 Mg database file.  The main reason I have this problem is because of embedded documents (plans, specs, news articles, etc).  I realize this is probably the most inefficient way to organize a database, however my database design abilities are extremely limited.  I tried linking to an existing location as opposed to embedding.  This didn't work as there are a few people who work with this database, and not all of them have access the the storage drive.

when it comes to linked databases I have had very limited results, here again my abilities are limited.

I don't mind learning a programing language if it will be worth the time and effort.

Thanks.

Sounds kinda of simple, (I do not know full data base specs though!) But with mysql it also supports embeding docuemnts/images but this is not the prefered way of doing things.

Once you have a simple website set up (You could host it or hosted by a provided) Most offer mysql/php hosting for relatively cheap.

You could have a list of documents/images on the server and just have links to them. So when displaying the information for a property you would also include the documents/images/files that are linked to it.

There many FREE open source mysql admin tools, on easy one to set up/configure is phpMyAdmin 

[www.phpmyadmin.net/](www.phpmyadmin.net/) 

The main choice is whether you would like to host the site your self, or external hosting company. What language  you are willing to learn.

Rubinboy's view
php go with mysql like a horse and carriage, pretty easy to learn and relatively simple

---

### Post by OffAxis on 2008-08-26
usually only the path to the article / document / picture is stored in the database. You can have a folder for each project, and can even code up a 'Create a new folder here' button or form to simplify it for new projects.

> This didn't work as there are a few people who work with this database, and not all of them have access the the storage drive.

I don't understand. The frontend (user forms and queries) and backend (tables) currently exist in a single file, right? So to access the data in the tables (or any part of the database, for that matter), any user has to have access to that single file, so...? The scope should be the same regardless.

> when it comes to linked databases I have had very limited results
There's a 'Database Splitter' wizard that can handle it for you. 
Be sure to backup before you try anything (Access has a lot of one-way streets). The backend and frontend, however, can always be re-integrated.

If you can provide more details on your set up we might be able to help you organize it a bit better.

---

### Post by cookdn on 2008-08-26
Had you considered using an pre-built application as a solution? 

From your brief description something like SugarCRM ([http://www.sugarforge.org/content/open-source/](http://www.sugarforge.org/content/open-source/)) should be able to serve your immediate needs. There would be a bit of a learning curve, but this would be focused on configuring SugarCRM around your business process rather hand-coding a bespoke solution.

Hope this helps.
David

---

### Post by zippyties on 2008-08-26
Right now I have 1 primary table that contains most of my data. this is linked to an input form, which I use to input everything into my database.

You can have a folder for each project, and can even code up a 'Create a new folder here' button or form to simplify it for new projects.

I like this idea, it would be great to have button at the bottom of the form that would make a new folder named after the project.  I suspicion though that this is way above my head.  Currently i have about 5 OLE fields I can drag and drop into.  How would I send the appended docs to the folder, all of this taking place within the input form?



I don't understand. The frontend (user forms and queries) and backend (tables) currently exist in a single file, right? So to access the data in the tables (or any part of the database, for that matter), any user has to have access to that single file, so...? The scope should be the same regardless.

Right now it's only me and when it is necessary for someone else to work on it I send the DB via the company FTP and receive it later.  My question though was with a veiw to future requirements.

Thanks for your quick help

---

### Post by drubin on 2008-08-26
Sounds like you are pretty new to programming. Do you have any experience with programming/programming languages before?

The way most Data bases work. (access is the exception to the rule because in actual fact is not a 100% data base) is that you have a data base running (doesn't matter where it is located) and Applications connect to the data base and get the data |update |insert it.

Now the BARE basic applications would the the simple data base editors where by you are updating each coloumn value for value....

Then you get the more complex applications such as the custom written ones that have these "forms" you have created and they choose where the which columns the data goes into.

I am going to give you some links that I think about be helpfull before getting into to the complexities of making programs/websites. 

You would first understand how data bases work, and how to use them.
[http://en.wikipedia.org/wiki/Database](http://en.wikipedia.org/wiki/Database)  -> Dont worry if you don't understand it all some of it is very technical
[http://en.wikipedia.org/wiki/Microsoft_Access](http://en.wikipedia.org/wiki/Microsoft_Access)

---

### Post by zippyties on 2008-08-26
I am pretty new to programming, I took some programming in High School, however none of that is useful under the present circumstances,  I have used a little Python and Ruby for graphic design but that is the same story.

I have a server and a website already, and I can get the company to hire a consultant to build it if that is necessary.

Basically what I was hoping for was a solution that also includes Ubuntu.  I seriously dislike windows, but I am required to use it on my computer at work.  I have a laptop with Ubuntu and I am hoping to find a solution that will allow me to use both to work on my database.

---

### Post by drubin on 2008-08-26
> **zippyties said:**
> I am pretty new to programming, I took some programming in High School, however none of that is useful under the present circumstances,  I have used a little Python and Ruby for graphic design but that is the same story.

I have a server and a website already, and I can get the company to hire a consultant to build it if that is necessary.

Basically what I was hoping for was a solution that also includes Ubuntu.  I seriously dislike windows, but I am required to use it on my computer at work.  I have a laptop with Ubuntu and I am hoping to find a solution that will allow me to use both to work on my database.

Great you have some back ground and understanding!! What OS is your server/website hosted on? 

I would still recommend hosting the system at your website company as they would more then likely take care of the boring stuff, Like hostnames, backups, internet connectivity(99% uptime). You can still write the code on your own laptop/desktop. but let the live version live there.

Have you ever used ubuntu as an OS before? if so how familiar are you with it?

MODS: I would suggest moving this to programming talk as you might get better answers.

---

### Post by zippyties on 2008-08-26
I don't know what OS the servers use, but I am willing to bet it's MS. I don't know if I am at liberty to give the Company name or URl under these curcumstances, I imagine it would be viewed as a security threat.

I switched to Ubuntu in July of 08', so I am still pretty green.

---

### Post by drubin on 2008-08-26
It is rather late, I will try and write a more details reply after work tomorrow. 

Hopefully this thread will be moved to the programming section and you get other help full replies before then.  

Glad you are sticking with it, and trying to learn new things

---

### Post by -Zeus- on 2008-08-26
I would recommend PostgreSQL or OODB.

---

### Post by nickgaydos on 2008-08-26
> **Thelasko said:**
> You might not like my answer, but OpenOffice.org has a database application that's very similar to Access.  It might even be compatible.

Yeap!

---

### Post by OffAxis on 2008-08-27
> I like this idea, it would be great to have button at the bottom of the form that would make a new folder named after the project. I suspicion though that this is way above my head. Currently i have about 5 OLE fields I can drag and drop into. How would I send the appended docs to the folder, all of this taking place within the input form?
That depends a little on how you have it configured currently, and how you'd like to setup a more streamlined system. It kinda sounds like you're upside down; instead of creating these OLE objects within the confines of Access and having them be embedded in your database, it's cleaner to store the path and just call the other program with the path as an argument. Take an excel spreadsheet for example. Instead of embedding it, you can open excel with
```
Dim stAppName As String

    stAppName = "excel.exe \\path\to\spreadsheet.xls"
    Call Shell(stAppName, 3)
```
Then you have the portability of modifying it within excel, too (with the full range of excel add-ins).
Simple matrices you wouldn't want to do that way, but then again simple calculations can be handled within access proper.

For simple file re-location (in lieu of the drag-and-drop you mentioned), you could script something in VBA or DOS, even. I think you can still put a custom path in the Windows SendTo Folder and shoot a file to wherever you want (so it's available in the Right-Click context menu).

Here's an example of some of the folder creation / file movement methods, just to give you some ideas. Please don't judge it too harshly (I didn't spend a whole lot of time on it).

---

### Post by OffAxis on 2008-08-27
No matter what db you use, if you're storing images & documents inside it you're going to hit a huge performance wall in a few years.

---

### Post by drubin on 2008-08-27
> **OffAxis said:**
> No matter what db you use, if you're storing images & documents inside it you're going to hit a huge performance wall in a few years.

With in Days you will see the knock on performance. store paths in the db, files on the file system.

---

### Post by OffAxis on 2008-08-27
> **rubinboy said:**
> With in Days you will see the knock on performance. store paths in the db, files on the file system.

oh hell ya, but he's at what, 768 MB after 6 months? So he's got about a year and half till the whole thing comes crashing down, and he loses everything.
Hopefully he'll get everything moved out before then:)

---

### Post by zippyties on 2008-08-27
Thanks for all your help guys,

I talked to my IT department this morning and they are going to look at opening a port so that I can use Kexi and/or Access as a front end for the corporate DB.

Also we are going to look at using the FTP site to link attachments from.  

Your advice was great!  

This really is what makes Linux better than MS.  The entire community/user base is interested in it's success and usability, as opposed to just the owners and operators of the company itself.  Linux may have alot of ground yet to cover, but it has greater momentum and better ideas than Apple and MS.

---

### Post by zippyties on 2008-08-27
I thought I would explain how on earth the attached files are so large.  The average set of construction plans in PDF are between 15 and 100 Mgs, and the associated special provisions can start at 5,000 pages and the sky is the limit, you guys know how legal contracts are:confused:

Thanks again!

---

