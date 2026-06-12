---
title: "Coy request for perl help"
date: 2007-05-29
forum: Programming Talk
---

### Post by DoctorMO on 2007-05-29
Hi all,

I'm developing the dohickey server side currently and was wondering if any of you programming types are up for giving me a hand? the task is very important as it allows the free flowing of hardware information wiki style and it interacts with the client (written in python) via xml over http.

[www.dohickey-project.com](www.dohickey-project.com)

I have the space set up, I have everything in CVS and I'm trying to move things forward but it just seems so difficult with just one person (lots of interest, but no real workers yet)

Any help would make me very happy.

Regards, DoctorMO

---

### Post by pmasiar on 2007-05-29
you can get completely free wiki at pbwiki.com - ready to use.

---

### Post by DoctorMO on 2007-05-30
as a replacement for the one I have at the moment?

---

### Post by DoctorMO on 2007-05-30
Sorry I should have made that clear; it isn't a wiki (although there is a wiki for the help pages) the software is based around the client and a fields setting method.

---

### Post by maniacmusician on 2007-06-01
[inconspicuous bump]

What this really involves is a thorough knowledge of Perl and MySQL. Here's how it works; the user downloads the client to their computer, runs it, fills in all the info about their hardware, adds some ratings, etc. Once they're done with that, the client uploads all the data to the server, which then parses it and stores it in a database. 

Now here's what still needs to be done, we need help with this:

-Write a search engine that will be able to effectively parse the database using different methods (by manufacturer, model, or simply keywords)

- Being able to browse the database through a web interface. Some discussion about this has occurred at the following thread: [http://ubuntuforums.org/showthread.php?t=457814](http://ubuntuforums.org/showthread.php?t=457814) 

- Being able to view complete and unique profiles uploaded by users in a presentable manner. So, this would mean being able to browse the database by entry and looking at each individual entry rather than just an average composite of them (which is also something that needs to be done). 

Thanks, any help would be appreciated.

---

### Post by DoctorMO on 2007-06-09
I'll take this as a no.

---

