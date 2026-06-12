---
title: "Suggested database software?"
date: 2010-09-02
forum: Programming Talk
---

### Post by rdbowers on 2010-09-02
I've been looking into mySQL for database construction, but I've found that the requirements mean that SQL just will NOT work (or people haven't been willing to tell me how to make it work).

I need to find database software that:

(1) It MUST be transportable- _I WILL NOT RENT SPACE ON A SERVER AND CANNOT USE THE DEFAULT LAYOUT (such as for SQL) FOR MOST OF WHAT WE WANT TO DO_ and need to build the database and then carry it to the organizations that will be using it (each organization will have its own database).  I need to be able to create database FILES... something that can be moved from computer to computer.  Or directories... it must be manageable and I will need to be able to do this while still in the learning curve.  Building the database on a server and then renting it the organizations won't work either!  IT MUST BE TRANSPORTABLE!

(2) multiple platforms- I expect the main ones will be Linux, Mac, and Windows.  

(3) Be able to handle large amounts of data- pictures, arrays of technical numbers, descriptions, etc.  There will be thousands to several tens of thousands of records.  It should be fast for that.  There will be a lot of searching and cross-referencing done with them when they are finished.  I expect multiple-gigabyte files when finished- for each database (one or more per organization).

(4) Be remotely accessible for management and maintenance.  (Not as important as the other requirements, but I don't particularly want to drive around the country all the time just to do minor changes.)

(5) Be able to be accessed by more than one workstation (one station can modify, but accessible by several).

AND THESE ARE ULTRA IMPORTANT:

(6) The software MUST be free (or  relatively cheap)- I am unemployed and cannot get unemployment- so I don't have money to spend.  The organization I will be doing this through has no money for software either (or minimal money).  We're hoping to generate income (for the organization and employment for myself) through these projects.

(7) Be relatively easy to learn and very flexible/powerful.  I'm hoping for something as easy to learn as Access or Approach.

(8) Once in place, the organizations will not need to learn how to program or anything like that- they will just need how to use the database and be able to do searches.


I thought SQL would be the answer to our needs, but it will not meet our requirements- especially the transportability issue (or, nobody will help me figure out how to do this).  The biggest problem with it is transportability.

Now as to my experience- I learned to program with C, Basic, and Fortran, and can read and diagnose some other languages.  I've been around computers since 1974, and am familiar with many different operating systems, but I'm still in the learning curve for Linux (started using it maybe a year ago).  I've worked with Access and Lotus Approach and built several databases using those packages.  I'm in the process of trying to learn SQL and possibly ASP, but need something I can pick up and start working with right away.

Any suggestions?

---

### Post by dv3500ea on 2010-09-02
Open Office Base is a free alternative to Access or Approach.

You can install it via the package [openoffice.org-base]("apt:openoffice.org-base").

---

### Post by TechnikAlsace on 2010-09-02
You may use mysql. It's free and it can be run on a local (apache based web-)server (I've even running one on my old IBM Thinkpad T42 notebook), no need to rent space elsewhere. For administration, install the (also free) phpmyadmin package. You may after development use phpmyadmin to export the whole database (structure and content) into one sql-file and be able to import it within seconds into another mysql instance elsewhere.

That's how I work since 5 years without generating costs for third-party software.;)

---

### Post by rdbowers on 2010-09-02
> **TechnikAlsace said:**
> You may use mysql. It's free and it can be run on a local (apache based web-)server (I've even running one on my old IBM Thinkpad T42 notebook), no need to rent space elsewhere. For administration, install the (also free) phpmyadmin package. You may after development use phpmyadmin to export the whole database (structure and content) into one sql-file and be able to import it within seconds into another mysql instance elsewhere.

That's how I work since 5 years without generating costs for third-party software.;)

OK!!!  THANK YOU!  That and another answer I just got a few minutes ago finally tells me how to use SQL for what I want to do!!!  

I'd been trying to learn SQL  and have mySQL installed (but barely gotten started).  I hoped that something like this could be done, but didn't know how, and most of the advice has been to go with space on a server or to use the default settings.  I admit I have a lot to learn, but need to do things in my own way and at my own pace (for multiple good reasons)- including knowing how to do some of the more complicated things up front, and learning the rest as I go along.

---

### Post by rdbowers on 2010-09-02
> **dv3500ea said:**
> Open Office Base is a free alternative to Access or Approach.

You can install it via the package [openoffice.org-base]("apt:openoffice.org-base").

I've got it, and was going to use it.  However, I was told (by an experienced programmer who is a friend) that when the file size gets huge, it becomes impossibly slow.  He said he'd tried it one time and after a few thousand records it slows to a crawl.  He suggested mySQL, but isn't available to give programming advice (or to look over my shoulder) now.

The file sizes I expect may be in the gigabyte range- maybe multiple gigabytes, as they may include multiple pictures and drawings for each item- and in some cases, tens of thousands of items.

---

### Post by kalaharix on 2010-09-02
SQLite is a file based database management system. It would not be quite as fast as mySQL but seems to meet your requirement for portability.

Only one user can modify SQLite although many can read at the same time.

Other responders to your question are correct. The fact that mySQL is 'server' based does not mean that it needs a separate machine. You do not even need Apache.
sudo apt-get install mysql-server
and
sudo apt-get install mysql-client
(both from terminal) are all you need to get going.

To move the database from one machine to another:
MySQLDump  the database to a text file. I then typically squeeze it with P7zip, send it over Dropbox, and redefine the database from mySQL at the other end.

Just an addendum: I find it easier to leave all root passwords blank during 'sudo apt-get install mysql-server'. I then use another management program (mySQLAdmin) to set the root password later.

---

### Post by Krupski on 2010-09-02
> **kalaharix said:**
> MySQLDump  the database to a text file. I then typically squeeze it with P7zip........

Good point. I explained to him in a different post how to do a dump and load of MySQL, but I forgot to tell him to compress the file!

Being a text file, the MySQL dump compresses very nicely.

---

### Post by xircon on 2010-09-02
Glom - [http://www.glom.org/wiki/index.php?title=Glom](http://www.glom.org/wiki/index.php?title=Glom)

Not used it yet, going to investigate this at the weekend.

---

### Post by Some Penguin on 2010-09-03
> **rdbowers said:**
> OK!!!  THANK YOU!  That and another answer I just got a few minutes ago finally tells me how to use SQL for what I want to do!!!  

I'd been trying to learn SQL  and have mySQL installed (but barely gotten started).  I hoped that something like this could be done, but didn't know how, and most of the advice has been to go with space on a server or to use the default settings.  I admit I have a lot to learn, but need to do things in my own way and at my own pace (for multiple good reasons)- including knowing how to do some of the more complicated things up front, and learning the rest as I go along.

You might also want to look at PostgreSQL.  It's also free, is quite cross-platform, and is quite respectable in functionality and performance.

Having used both MySQL and PostgreSQL for fairly non-trivial workloads (tables reaching perhaps 20M rows, lots of fairly complex queries) both are quite usable.  PostgreSQL's lack of an "INSERT OR UPDATE" is slightly obnoxious, but it's lack of data-corruption issues (modulo a certain bug that can result in corrupt dumps on OS X -- basically, broken isspace() combined with some dubious logic applied to certain multibyte UTF-8 characters) is nice, and pl/pgsql is rather handy.  On-the-fly replication doesn't seem that critical for you (but you *should* think about an off-site backup strategy, because losing client data is doubleplus ungood).  Materialized views aren't supported directly, although you can (carefully...) emulate them with triggers.

To dump/restore PostgreSQL database, 'pgdump' / 'pgrestore'.
To dump an individual table, '\COPY from/to' can be quite fast.  mysql has similar functionality.  I make heavy use of such things as I tend to do a fair bit of computing on the ec2 cloud and then export the results the boxes that'll need 'em.

And both run as servers, but both can be configured for local or remote access.  Both have bindings for Perl and Java, as well as other languages.  Both have fairly significant communities... although I have more faith in the PostgreSQL team than I do in Oracle's willingness to support a free database.

That said... I would be a bit reluctant to shove actual pictures in a database.  I might put identifiers and other metadata for the pictures into a database, but there's not much reason to put data that is not very query-able into a database.  Chances are that you won't need to actually write queries that depend upon the actual bytes within the images.

---

