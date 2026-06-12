---
title: "Logging to File or Database"
date: 2009-01-28
forum: Programming Talk
---

### Post by pcman312 on 2009-01-28
I'm looking to build a basic php logging system for my new website and I'm wondering what everyone's opinion is regarding whether to put the log messages into a database or to a flat file. Both methods are fast enough, so speed isn't a critical issue here. It wouldn't be a very complex system, just date/time, a basic level (INFO/WARNING/ERROR), and the message itself. The database choice would involve creating a web interface to the logs (which would only be accessed via an admin page), and would be searchable and sortable. The flat file would be quicker to develop, but wouldn't provide the functionality of searching/sorting.

Anyway, I'm just looking for opinions on which would be the better choice.

---

### Post by myrtle1908 on 2009-01-28
Unless your logfile will remain relatively small, a database is preferable.  If you have experience with SQL then knocking something up shouldn't take long at all.  I recommend MySQL.

---

### Post by slavik on 2009-01-28
the complex a system is, the more chance for something to break. I vote for flat file. What kind of sorting would you need? What if the db gets corrupted and you need the log file?

---

### Post by ufis on 2009-01-28
I'd go for flat file too.

If you format the flat file in say csv format it would be as simple to build a web interface (with the same functionality*) reading the flat file as it would be for the DB backend.

*For your logging that looks to be a small amount of data.

---

### Post by monkeyking on 2009-01-28
as long as my data remains on the nice side of 1 gig i use flatfiles.

---

### Post by pcman312 on 2009-01-29
Good thoughts. I think I'm going to stick with the flat file system and make a simple web front end to the log.

Thanks everyone for your input!

---

