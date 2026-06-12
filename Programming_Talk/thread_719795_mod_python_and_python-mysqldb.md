---
title: "mod_python and python-mysqldb"
date: 2008-03-09
forum: Programming Talk
---

### Post by kaptainlange on 2008-03-09
I've recently become a big fan of python, and as an attempt to become better at it, I want to rewrite my php+mysql website in python.

I'm running Apache with mod_python installed, and that all seems to be working just fine.  I just keep running into problems with python-mysqldb.  I keep getting strange errors that I have no clue how to fix.  For example, I am currently getting this error:

```
File "/srv/web/vhosts/dev.scarybear.net/html/blog.html", line 17, in 
    for c in post.get_children():

  File "/srv/web/vhosts/dev.scarybear.net/post.py", line 86, in get_children
    cursor.execute(query, param)

  File "/usr/lib/python2.5/site-packages/MySQLdb/cursors.py", line 145, in execute
    charset = db.character_set_name()

InterfaceError: (0, '')
```

The interesting thing about this is that I am performing queries before this point that work just fine.

I've tried all manner of handling of the database.  Originally I would connect to the database in a config file that was included across the site, however this would eventually lead to a timeout if no requests were sent for a while, resulting in a "MySQL server has gone away" message.  So then I decided to initiate a connection per request by including it in the right spot, which results in this error now.

What is happening is the publisher handler calls index.index() which creates the connection globally, meaning it creates a connection at conf.DB.  Then the other modules I have that utilize the db are just supposed to use conf.DB.  This seems to work sometimes but as you can see other times fails.

In case it helps, this is the code that fails:
```
		
79 query = \
80           """SELECT child_post_id
81           FROM rel_posts
82           WHERE parent_post_id = %s """
83
84 param = (self.id,)
85 cursor = self.db.cursor(DictCursor)
86 cursor.execute(query, param)
```

Is there a better or more correct way of handling database connections with mod_python or python in general?  Something that would just let me continue development at the very least.  This is becoming a show stopper for me, but it has to possible to get around.  Stuff like Django would never work if they had this problem.

EDIT:
I solved this, I feel stupid for letting it take this long.  The reason it was giving this error was because I was closing out the db connection before I actually called that code, or rather before psp.PSP called that code.  To be fair to myself, it isn't readily apparent that psp isn't calling that code until the end of the request.

---

### Post by pmasiar on 2008-03-09
You may consider looking at Django or Turbogears web app framework. Especially TG allows you to use your choice from multiple templating modules and ORM wrappers, while solving most of the boring problems for you.

---

