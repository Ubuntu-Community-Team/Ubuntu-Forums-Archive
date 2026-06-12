---
title: "Would you use Ubuntu to work on a SQL Server web project?"
date: 2008-10-10
forum: Programming Talk
---

### Post by tc101 on 2008-10-10
I just got an offer to work on an old web based system written in old ASP (not ASP dot net, but the original ASP) and SQL Server.  I am not enthusiastic about the technology, but I can do this working at home part time, the money is good, and I need work, so I am going to take it.

I don't have a windows computer at home.  I can do all the ASP just using a text editor and testing it on the site.  That will not be a problem.  I am not sure how practical it will be to do the SQL scripts though.  I can test them on the site.  Can I test them on my desktop using mySQL or are there too many minor differences?  Is there something like MS Query Analyzer that runs on Ubuntu?  

What do you think?  Should I install windows, or get a windows computer, or can I do this on Ubuntu?

---

### Post by dwhitney67 on 2008-10-10
I've pondered the same question myself.

For instance, why doesn't the US Gov't have faith in Ubuntu?  Why is it that they put faith in Red Hat, and on occasion Fedora, but not Ubuntu.

Just questions in my mind... don't get offended Ubuntu lovers.  I use Ubuntu too, but my fave is Fedora.

---

### Post by mike_g on 2008-10-10
AFAIK you can pay to get guaranteed support with Red Hat and SuSe. Ubuntu dosent offer that and thats why many of the bigger companies go for Red Hat Linux.

---

### Post by dwhitney67 on 2008-10-10
> **mike_g said:**
> AFAIK you can pay to get guaranteed support with Red Hat and SuSe. Ubuntu dosent offer that and thats why many of the bigger companies go for Red Hat Linux.
Ha!  You think that Canonical wouldn't work for a penny or two?  They are in business just like the other outfits.  Red Hat, SuSe, Mandriva, and Ubuntu are peddling support; in every case, the Linux product is free.

When Ubuntu starts shipping their product with SELinux enabled (by default), then maybe, just maybe, some gov'ts will consider it worthy.  I must add that starting with Ubuntu 8.04, that SELinux is available, but only as an option... in other words, it must be installed after the base OS is installed.

P.S.  My opinion is biased because I have a close "contact" that supports [IA]("http://www.nsa.gov/selinux/") efforts with the No Such Agency.  Maybe Ubuntu will be considered in the near future, but as of yet, I have heard no positive indication that it will.

---

### Post by DrMega on 2008-10-10
> **tc101 said:**
> I just got an offer to work on an old web based system written in old ASP (not ASP dot net, but the original ASP) and SQL Server.  I am not enthusiastic about the technology, but I can do this working at home part time, the money is good, and I need work, so I am going to take it.

I don't have a windows computer at home.  I can do all the ASP just using a text editor and testing it on the site.  That will not be a problem.  I am not sure how practical it will be to do the SQL scripts though.  I can test them on the site.  Can I test them on my desktop using mySQL or are there too many minor differences?  Is there something like MS Query Analyzer that runs on Ubuntu?  

What do you think?  Should I install windows, or get a windows computer, or can I do this on Ubuntu?

There are a few subtle differences between MySQL and MSSQL flavours of SQL, but if you are just using SQL-92 commands (select, insert, update, delete) on an existing database schema, you should be OK for the most part.

The way I would do it is to get the free version of SQL from MS, and install it in WINE. It works because I have it on my machine, but in my case I use Visual Studio through WINE. I would then develop and test all my SQL bits and pieces, and then once happy with them, build them into ASP functions to include in your main app.

---

### Post by kernelhaxor on 2008-10-10
I would suggest using Windows.  Not sure if visual studio supports classic ASP?  If u use Windows, u can also use SQL Server Management Studio for all ur SQL .. I wud imagine development & testing would be much faster on Windows 

I used to use a Windows virtual machine for ASP .net dev work ..

If you have to use linux, have you checked out [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by LaRoza on 2008-10-10
> **dwhitney67 said:**
> 
For instance, why doesn't the US Gov't have faith in Ubuntu?  Why is it that they put faith in Red Hat, and on occasion Fedora, but not Ubuntu.


Perhaps because Ubuntu is relatively new.

Why would a government use an OS which is four years old? How many times do they switch OS's?

---

### Post by directhex on 2008-10-10
Original ASP has very little in common with ASP.NET, and I don't know of any Linux-based solutions worth your time. Sorry.

---

### Post by lykwydchykyn on 2008-10-10
Where I work I have MySQL, Postgresql, and Oracle to deal with (we have MSSQL too, but I steer clear of having to work on those).  In my experience, the differences between those three are enough to keeping me googling syntax to write even fairly simple queries.  

My advice is to get a development environment as close to the production environment as possible.  If it saves you even one bug, it's worth it.

---

### Post by Rich78 on 2008-10-10
Trial and error on the server is not a good idea as it won't always show up your problems.

You'd be best running a VMware Windows image and installing SQL Server Express edition.  You could also install VS.NET Express for an environment if you wish, it doesn't matter if it's old asp.

Express editions are freely downloadable from msdn.

I agree it's best to get your environment as close to production as possible.

---

### Post by tc101 on 2008-10-10
From what everyone is saying, I guess I should get a windows environment if I do this project
 
 I can think of 3 ways to get the windows environment:

1. Wine - I have never used it but people seem to be happy with it

2. VMware Windows image.  I had never heard about it but I just read a little about it on Wikipedia.  I am not clear how this differs from Wine or which would be better.

3. I was going to get a new Dell pretty soon.  Rather than get it with Ubuntu installed I would just get it with windows and then set up a dual boot system for ubuntu.

Any suggestions would be appreciated.

---

### Post by lykwydchykyn on 2008-10-10
Install virtualbox-ose from the repos and grab a copy of the windows install disc.  That's your best bet.

Wine is sort of a translator that takes Windows system/API calls and translates them into Linux calls (ok bad explanation).  Point being, it's a simulation of the Windows API for programs to run on.

VMWare/VirtualBox are virtual machines.  They emulate a computer, which you then run Windows on.  

It really depends on whether your hardware is capable of running a VM with Windows and whether or not you have a Windows install CD and license.

---

### Post by tc101 on 2008-10-11
> It really depends on whether your hardware is capable of running a VM with Windows and whether or not you have a Windows install CD and license.

I don't have a windows CD so I think I'll try wine.  I'll see if I can run the free MS SQL Server query analizer in wine and go from there.

---

### Post by pmasiar on 2008-10-11
> **dwhitney67 said:**
> why doesn't the US Gov't have faith in Ubuntu?  Why is it that they put faith in Red Hat, and on occasion Fedora, but not Ubuntu.

Because they are bureaucrats, who use different selection criteria than mere humans? ;-)

Also, NSA uses RH for strong security, so they may have some internal rules about that.

Other (non-USA) government have no such problems, I am aware of Andalusia (a province in Spain) which uses Ubuntu on all gov comps, there might be more.

---

### Post by drubin on 2008-10-11
> **dwhitney67 said:**
> I've pondered the same question myself.
For instance, why doesn't the US Gov't have faith in Ubuntu?  Why is it that they put faith in Red Hat, and on occasion Fedora, but not Ubuntu.
Just questions in my mind... don't get offended Ubuntu lovers.  I use Ubuntu too, but my fave is Fedora.

How did this comment come up? Was redhat/Fedora ever mentioned :s

> **lykwydchykyn said:**
> Where I work I have MySQL, Postgresql, and Oracle to deal with (we have MSSQL too, but I steer clear of having to work on those).  In my experience, the differences between those three are enough to keeping me googling syntax to write even fairly simple queries.  

My advice is to get a development environment as close to the production environment as possible.  If it saves you even one bug, it's worth it.
+1 If the servers are hosted on windows (and they have to stay like that?) work on a development server. There might be a bug spesific to windows that you will never notice until the system is put live.

---

### Post by tc101 on 2008-10-11
I was thinking of doing the project on my ubuntu computer.  I installed Wine, then learned that I had to install .Net before I could install SQL Server Express.  I started reading about all the problems people have had with .Net running in wine and at this point I think I will probably just spend $500 and buy a cheap windows computer from Dell and use that for the project.  I will eventually install ubuntu on the windows computer and set it up for dual boot.  I need a new computer anyway.

---

### Post by LaRoza on 2008-10-11
> **pmasiar said:**
> Because they are bureaucrats, who use different selection criteria than mere humans? ;-)

Also, NSA uses RH for strong security, so they may have some internal rules about that.

Ubuntu hasn't come with SELinux, which is a factor. 

[http://en.wikipedia.org/wiki/Selinux](http://en.wikipedia.org/wiki/Selinux)

---

### Post by lykwydchykyn on 2008-10-12
Of course, you could always try talking the client into scrapping the old system and having it rewritten in something open like php, java, or python.  Sooner or later they'll have to ditch that old ASP code.

---

### Post by DrMega on 2008-10-12
> **tc101 said:**
> 

3. I was going to get a new Dell pretty soon.  Rather than get it with Ubuntu installed I would just get it with windows and then set up a dual boot system for ubuntu.

Any suggestions would be appreciated.

If you have to develop in asp.net and MSSQL, and a Windows box is an option, I would definately go down that route.

If you have to get it going on Ubuntu, I know that VS2005 works under WINE. I have it installed and working on my machine, but I haven't used it that much at home, so there is no way to be certain that it is 100% compatible in every scenario.

---

