---
title: "Php caching? or database end?"
date: 2013-06-16
forum: Programming Talk
---

### Post by jairoh_ on 2013-06-16
I have a site that would pretty much looked like a forum and the topic threads are in bold. 
So what i want is when a specific user visit's that thread, the next time he will see its title it will be unbold unless a new user replied to that thread. like in this forums. any suggestions on how to do it? or algorithms? I would appreciate if you have so. I'm new to web developing. thanks.

---

### Post by SeijiSensei on 2013-06-16
If you have little or no experience with web development, I think you would be much better off using existing forum software.  While vBulletin, which is used here, isn't free, it would be my first choice.  Among free alternatives you should look at Simple Machine Forum or phpBB.

That said, if you are committed to reinventing the wheel, then you would manage this task in an SQL database.  If you look at how this forum is organized, each thread has a identification number (for this one it is 2155023), as does each posting.  (Your posting above has ID 12694228.  Place your cursor over the "#1" on the right-hand side of your post's header line and look at the link to which it points.)  In the database you would have a table that consists of three fields, the user's ID, the thread's ID, and the ID number of the last posting read.  Each time a user reads a post you would update the table.  When the user logs in next time, you can determine if there are unread posts in the thread and proceed accordingly.

---

### Post by jairoh_ on 2013-06-17
> **SeijiSensei said:**
> If you have little or no experience with web development, I think you would be much better off using existing forum software.  While vBulletin, which is used here, isn't free, it would be my first choice.  Among free alternatives you should look at Simple Machine Forum or phpBB.

That said, if you are committed to reinventing the wheel, then you would manage this task in an SQL database.  If you look at how this forum is organized, each thread has a identification number (for this one it is 2155023), as does each posting.  (Your posting above has ID 12694228.  Place your cursor over the "#1" on the right-hand side of your post's header line and look at the link to which it points.)  In the database you would have a table that consists of three fields, the user's ID, the thread's ID, and the ID number of the last posting read.  Each time a user reads a post you would update the table.  When the user logs in next time, you can determine if there are unread posts in the thread and proceed accordingly.

i kinda get your concept sir. gonna update soon. thank you.

---

### Post by lisati on 2013-06-17
Another php-based example of forum software that has enjoyed some popularity here is [MyBB]("http://www.mybb.com/").

---

### Post by jairoh_ on 2013-06-17
> **lisati said:**
> Another php-based example of forum software that has enjoyed some popularity here is [MyBB]("http://www.mybb.com/").
no sir. i want to make my own for a school project. :D

---

