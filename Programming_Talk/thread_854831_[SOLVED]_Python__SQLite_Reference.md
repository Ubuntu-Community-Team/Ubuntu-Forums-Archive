---
title: "[SOLVED] Python / SQLite Reference"
date: 2008-07-09
forum: Programming Talk
---

### Post by Yuki_Nagato on 2008-07-09
I am completely new to the world of database scripting and CGI.  So the least I need is a reference to these libraries and such.  Google turns up many old things that are now outdated and un-useful.

Does anyone have any materials I can use?

---

### Post by Can+~ on 2008-07-09
Personally, I used the python documentation:

[http://docs.python.org/lib/module-sqlite3.html](http://docs.python.org/lib/module-sqlite3.html)

---

### Post by Yuki_Nagato on 2008-07-09
> **Can+~ said:**
> Personally, I used the python documentation:

[http://docs.python.org/lib/module-sqlite3.html](http://docs.python.org/lib/module-sqlite3.html)

Excellent.  Just what I needed.  However, modifying the code to match my needs, (and to make sure it works) I stumble across this error in the server logs:

```
conn = sqlite3.connect('XXXX')
NameError: name sqlite3 is not defined
```

I heard that SQLite comes bundled with python.  Am I perhaps missing something because of my installation from repositories?

---

### Post by elithrar on 2008-07-09
First try:

```

import sqlite3

```

---

### Post by Yuki_Nagato on 2008-07-09
```
#!/usr/bin/python

import cgi
import sqlite3

conn = sqlite3.connect('/tmp/example')

c = conn.cursor()

# Create table
c.execute('''create table stocks (date text, trans text, symbol text, qty real, price real)''')

# Insert a row of data
c.execute("""insert into stocks values ('2006-01-05','BUY','RHAT',100,35.14)""")

# Save (commit) the changes
conn.commit()

# We can also close the cursor if we are done with it
c.close()
```

It is copied from the link above from the documentation.  It spits out a "Premature end of script headers" error.  I have run other scripts successfully.

I do not have to edit the httpd.conf file to make this work, do I?  I have not set up any code to deal with databases.

---

### Post by elithrar on 2008-07-09
I'm unable to replicate the issue on my local box, but you won't need to touch httpd.conf - the script only relies on the CGI library in Python, not on a web server. As for databases, sqlite is a file-based database - the script is the beginning and end of any "setup" you need to do.

Can you post the error you're getting verbatim?

---

### Post by pmasiar on 2008-07-09
You have two separate problems, CGI and SQL. Last error is from CGI.

Consider using Django, it will simplify your SQL and make your CGI more organized - and will nudge you to use templates instead of hardcoding HTML.

Check also wiki in my sig: Simple web app (3 lines), just to make sure your web server is configured properly. Or use Django directly.

---

### Post by Yuki_Nagato on 2008-07-09
Alright.  I will knock around with Django for a while.

And the error is as follows.

```
[Wed Jul 09 23:27:16 2008] [error] [client ---.---.---.---] Premature end of script headers: test.py, referer: http://---.---.---.---/html/test.html
```

---

### Post by pmasiar on 2008-07-10
Looks like you do not send HTML-formatted page as response to (output from) CGI script.

add 'import cgitb; cgitb.enable()' (and read up on CGI traceback)

---

### Post by Yuki_Nagato on 2008-07-10
Thank you very much, all of you, for your help.  I am, however fed up with this.  All I need is a SELECT statement in a few places and the CGI to plant it in the page.  

I am instead going to use the Python code to pull text from Text files and plant that into the requested HTML pages.  I was able to do that in the past.  I will be back on if more trouble arises.

Thank you, and this thread is considered solved.

---

