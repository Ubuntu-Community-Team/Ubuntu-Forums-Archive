---
title: "Building Job Site -- Need Search Performance Advice"
date: 2008-08-02
forum: Programming Talk
---

### Post by SuperMike on 2008-08-02
My client wants me to build a job search/post site. I've done many PHP5/MySQL5 sites and have used the MATCH/AGAINST keyword search syntax, although I think a site of this stature might really slow down the system tremendously. I'd like to throw out some options, and perhaps you can give me your opinion, especially with experience if you have it. Please also realize for now we're going with a shared hosting plan until the site has enough ad revenue to move into better, more dedicated hosting plans.

* Implement the search with MATCH/AGAINST syntax on MySQL5. As the site grows, just upgrade to better web plans and beefier hardware. Eventually introduce a web farm and a separate, central database with a replication schedule to another database.

* Implement the search on PostgreSQL because it's proven to scale better than MySQL5. Again, as site grows, go for better web plans, beefier hardware, and then eventually implement a web farm with central database.

* Don't use a database for the job seeker profiles or the posted jobs. Store them as static HTML as files on the filesystem, and implement a way in PHP (securely, if I can figure it out) to write these files to the filesystem as they are created, as well as permit someone to re-edit these files and remove them as well. Then, just implement Google Search into the site.

* Same as last bullet, but instead of Google Search, use some other F/OSS-based search tool. (My concern is which tool works well in a shared hosting environment where I'm only allowed to install PHP stuff and MySQL stuff, not binary files and not custom compiling?)

---

### Post by pmasiar on 2008-08-02
Lucene (Java)/PyLucene is good full-text search tool

---

### Post by drubin on 2008-08-02
> **pmasiar said:**
> Lucene (Java)/PyLucene is good full-text search tool

Indexing can be a very HUGE complex task or a very simple task...

There are 2 branches of solutions that you have hinted at.

**Edit**Hard ware option is not that greatest! Also would be hard to implement being on a shared hosting enviroment

1) Hard Ware
You could use a very very simple algorims/software and  just PUMP up the hard ware and hope that it is fast enough.

2) Soft Ware
You can research indexing algorithms and try and implement the one that best suites your need. Some of them can HUGELY reduce the amount of hard ware that is required to process them :) 

For a basic idea about searching, Compare the difference between a Linear search and a Binary search.
[http://en.wikipedia.org/wiki/Binary_search](http://en.wikipedia.org/wiki/Binary_search)
[http://en.wikipedia.org/wiki/Linear_search](http://en.wikipedia.org/wiki/Linear_search)

All that indexing does it provides a "look up"/key table information that is ALOT easier to search through that contains links/locations to the actual data.



PS
Or maybe try and use Google. They have a site search functionality built in where by you can use google to search/scan your own website.(As long as the data is not sensitive.)

**EDIT:** Just re-read the alst part of the post you already hinted at it... :)

---

### Post by SuperMike on 2008-08-02
> **pmasiar said:**
> Lucene (Java)/PyLucene is good full-text search tool

I'm not certain, but I thought that Lucene could not easily be installed on a site that's setup with a PHP5/MySQL5/Linux hosting plan. I use a2hosting.com. Can anyone confirm or deny?

---

### Post by pmasiar on 2008-08-02
Maybe you need to look around for more flexible hosting, a notch above bottom-price?

Sorry I cannot help you with this area, we have more than enough blades in our server room, so I do not follow commercial hosting, but as they say, you get what you paid for :-)

---

### Post by drubin on 2008-08-02
> **pmasiar said:**
> Maybe you need to look around for more flexible hosting, a notch above bottom-price?

Don't assume it needs Hard Ware/3rd party applications to solve issue's...

I have always been puzzled by the MS engineer mentality so the solution is to slow throw so more hard ware/memory at the problem to solve the solution.

---
This brings me back to a discussion that I had with a friend of mine about indexing XML files for his university project. Basically the the task was to use indexing to search for word/phrases embedded in about 4000 xml files.

To say the least a simple linear search line by line through the files was in no way an option(Nor was it part of the assignment, clever lectures). Many people in his class decided to choose the devil they knew rather then the devil they didn't and used Java to index the files. (Took about 1min). Others decided they would go the C++ route they got thiers down to about 30-40 seconds. He decided to go the Perl route... (he got it to under 10 seconds)

Now real amazing thing about this is to know what to use when. (and how to use it). He used simple regular expressions to strip out all the XML tags. (who cares about them any way it was the data that was important).

Created some simple look up files with references for each word the file and the line number.

Now when trying to do a search for a particular word you only have to search the index file for the key word and it will give you the line file/line where it was located. 

You choose the solution that best suites your current requirements/resources...

---

### Post by SuperMike on 2008-08-02
Excellent points, Rubinboy.

Still, after much interaction with me on the web from various points, it appears the thing I keep hearing is to use Sphinx with LAMP on a Virtual Private Server (VPS) hosting plan. The reason for VPS is because Sphinx is a custom compile, and no shared hosting plan on the planet will let you do a custom compile of Sphinx.

Anyone know of a Debian or Ubuntu VPS hosting plan that lets me have root, ssh, and installation of my own stuff? (I would prefer Ubuntu.) My client can afford about < $500/year USD VPS hosting plans for now and then scale up as necessary after that.

---

### Post by drubin on 2008-08-02
[http://webhosting.net/products_and_services_virtual_hosting.aspx](http://webhosting.net/products_and_services_virtual_hosting.aspx)

---

### Post by SuperMike on 2008-08-02
> **rubinboy said:**
> [http://webhosting.net/products_and_services_virtual_hosting.aspx](http://webhosting.net/products_and_services_virtual_hosting.aspx)

Thanks. I didn't see anything about Debian or Ubuntu there. Do you know if they support these?

---

### Post by drubin on 2008-08-02
> **SuperMike said:**
> Thanks. I didn't see anything about Debian or Ubuntu there. Do you know if they support these?

I think they support any operating system you would like, When I used them a while back they asked what OS I would like to use so maybe..

---

### Post by SuperMike on 2008-08-02
> **rubinboy said:**
> maybe..

Okay, I'll contact them. Thanks for the tip.

---

### Post by mssever on 2008-08-03
Someone once recommended [http://slicehost.com/](http://slicehost.com/) to me. It looks like a great option, but I haven't tried them since they're overkill for my needs.

---

### Post by SuperMike on 2008-08-03
> **mssever said:**
> Someone once recommended [http://slicehost.com/](http://slicehost.com/) to me. It looks like a great option, but I haven't tried them since they're overkill for my needs.

Don't quote me on this, but I don't think that slicehost.com lets you pick your flavor of Linux, which is important to me. I'm a fan of Debian and Ubuntu Server, although I prefer Ubuntu Server.

---

### Post by mssever on 2008-08-03
> **SuperMike said:**
> Don't quote me on this, but I don't think that slicehost.com lets you pick your flavor of Linux, which is important to me. I'm a fan of Debian and Ubuntu Server, although I prefer Ubuntu Server.
According to their website:
[quote=http://www.slicehost.com/questions/#distros]**Which distributions do you offer?**      
Currently the following distributions are available for install
       
[LIST]
[*]Ubuntu 8.04.1 (Hardy Heron) LTS
[*]Ubuntu 7.10 (Gutsy Gibbon)
[*]Ubuntu 6.06 (Dapper Drake) LTS
[*]Debian 4.0 (Etch)
[*]Gentoo 2007.0
[*]Centos 5.2
[*]Fedora 9
[*]Arch 2007.08
[/LIST]
[/quote]

---

### Post by slavik on 2008-08-03
afaik a VPS is when you have a virtual machine all to yourself (VMWare, kvm, xen, etc.) which is usually more expensive than a simple virtual host (handled by apache).

---

### Post by drubin on 2008-08-03
> **SuperMike said:**
> Don't quote me on this, but I don't think that slicehost.com lets you pick your flavor of Linux, which is important to me. I'm a fan of Debian and Ubuntu Server, although I prefer Ubuntu Server.

ubuntu server is not stable enough for the "scale" you are wanting to get to. I would rather recommend using Debian Etch. There are a few references to why Ubuntu server not the preferred server platform.

CentOS is highly stable and use it for all my commercial hosting (if i have a choice)

---

### Post by SuperMike on 2008-08-03
> **slavik said:**
> afaik a VPS is when you have a virtual machine all to yourself (VMWare, kvm, xen, etc.) which is usually more expensive than a simple virtual host (handled by apache).

Yep. A VPS costs more, but it's for the person who is somewhere on the budget between shared hosting and dedicated hosting. They can't afford dedicated hosting yet, but want something close as far as benefits. One of those benefits (unless you use the dorks at Dreamhost.com) is to get the power to install your own stuff.

---

### Post by SuperMike on 2008-08-03
> **rubinboy said:**
> ubuntu server is not stable enough for the "scale" you are wanting to get to...

Got proof?

---

### Post by drubin on 2008-08-04
> **SuperMike said:**
> Got proof?

Do a quick search on google,  Sorry i am currently at work and do not have the time to find it quickly. But it simply has to do with ubuntu is a branch of the unstable Debian branch and Debian is more thoroughly tested before it is released then ubuntu.

---

### Post by Reiger on 2008-08-04
What is the kind of searching you want to do? Because you may be able to cheat a little by building a server side search layer which caches "most popular" & 'redirects' searches based on generic categories.

For instance if you have something sort-able by city; you can already implement a list of "cities". If someone searches for a job inside city x but x isn't in the list you can immediately say "Sorry, no dice." before you have even attempted to search the data base...

Also I presume you thought of the possibilities of creating & defining views inside your data base?

---

### Post by SuperMike on 2008-08-04
> **rubinboy said:**
> Do a quick search on google,  Sorry i am currently at work and do not have the time to find it quickly. But it simply has to do with ubuntu is a branch of the unstable Debian branch and Debian is more thoroughly tested before it is released then ubuntu.

What I heard was that the Debian guys were slooooooow. What Ubuntu does by using the unstable branch is to make a stable branch off the unstable branch, thereby fixing this problem but only if you use Ubuntu. It lets Ubuntu get more up to date stuff than other Linuxes, but has the testing necessary to make a stable one. I would reason to bet with Launchpad that there are far more bugs fixed with Ubuntu than there are with Debian.

---

### Post by SuperMike on 2008-08-04
> **Reiger said:**
> What is the kind of searching you want to do? Because you may be able to cheat a little by building a server side search layer which caches "most popular" & 'redirects' searches based on generic categories.

For instance if you have something sort-able by city; you can already implement a list of "cities". If someone searches for a job inside city x but x isn't in the list you can immediately say "Sorry, no dice." before you have even attempted to search the data base...

Also I presume you thought of the possibilities of creating & defining views inside your data base?

**Kind.** The three fields would be keywords, city & state (or zip) [only if you want proximity], and job category. The job category list would be almost a 100% copy of hotjobs.com. When users click Advanced Search (which, by the way, is only available after you do the regular search), it will look somewhat like this:

[http://hotjobs.yahoo.com/jobs-search-advanced](http://hotjobs.yahoo.com/jobs-search-advanced)

**Caching.** I don't know how to do that in MYSQL or with PHP. Please share.

**Views.** Are there sensational performance benefits of using MYSQL views?

---

### Post by drubin on 2008-08-04
> **SuperMike said:**
> What I heard was that the Debian guys were slooooooow. What Ubuntu does by using the unstable branch is to make a stable branch off the unstable branch, thereby fixing this problem but only if you use Ubuntu. It lets Ubuntu get more up to date stuff than other Linuxes, but has the testing necessary to make a stable one. I would reason to bet with Launchpad that there are far more bugs fixed with Ubuntu than there are with Debian.

Disagree, I personaly think Ubuntu is the way to go for desktop PC, where by a little down time is ok, but for servers I would still not recommend it. I will try and dig up the resources that I found about this. :)

But in the end the choice is yours.

---

