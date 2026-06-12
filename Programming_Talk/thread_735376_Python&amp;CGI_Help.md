---
title: "Python&amp;CGI Help"
date: 2008-03-25
forum: Programming Talk
---

### Post by PyPhreak on 2008-03-25
Hello everyone,I am having some trouble,running a Python/CGI file on my browser,I have Apache installed,and have Python 2.5.2..but when I open a CGI file I get the source code in the browser...I have no idea how to see what I am trying to do..it should be a simple bulletin board..
I am going to give the source of the Python and CGI files:
**Test.py**
[PHP]
import psycopg

conn = psycopg.connect('user=root  dbname=x')

curs = conn.cursor()



reply_to = raw_input('Reply to: ')

subject = raw_input('Subject: ')

sender = raw_input('Sender: ')

text = raw_input('Text: ')



if reply_to:

    query = """

    INSERT INTO messages(reply_to, sender, subject, text)

    VALUES(%s, '%s', '%s', '%s')""" % (reply_to, sender, subject, text)

else:

    query = """

    INSERT INTO messages(sender, subject, text)

    VALUES('%s', '%s', '%s')""" % (sender, subject, text)



curs.execute(query)

conn.commit()

[/PHP]
**Postgredb.sql**
[PHP]
CREATE TABLE messages (

    id          SERIAL PRIMARY KEY,

    subject     TEXT NOT NULL,

    sender      TEXT NOT NULL,

    reply_to    INTEGER REFERENCES messages,

    text        TEXT NOT NULL

);
[/PHP]
**Edit.cgi**
[PHP]
print 'Content-type: text/html\n'



import cgitb; cgitb.enable()



import psycopg

conn = psycopg.connect('dbname=x user=root')

curs = conn.cursor()



import cgi, sys

form = cgi.FieldStorage()

reply_to = form.getvalue('reply_to')



print """

<html>

  <head>

    <title>Compose Message</title>

  </head>

  <body>

    <h1>Compose Message</h1>



    <form action='save.cgi' method='POST'>

    """



subject = ''

if reply_to is not None:

    print '<input type="hidden" name="reply_to" value="%s"/>' % reply_to

    curs.execute('SELECT subject FROM messages WHERE id = %s' % reply_to)

    subject = curs.fetchone()[0]

    if not subject.startswith('Re: '):

        subject = 'Re: ' + subject



print """

    <b>Subject:</b><br />

    <input type='text' size='40' name='subject' value='%s' /><br />

    <b>Sender:</b><br />

    <input type='text' size='40' name='sender' /><br />

    <b>Message:</b><br />

    <textarea name='text' cols='40' rows='20'></textarea><br />

    <input type='submit' value='Save'/>

    </form>

    <hr />

    <a href='main.cgi'>Back to the main page</a>'

  </body>

</html>

""" % subject

[/PHP]

**Main.cgi**
[PHP]
print 'Content-type: text/html\n'



import cgitb; cgitb.enable()



import psycopg

conn = psycopg.connect('dbname=x user=x')

curs = conn.cursor()



print """

<html>

  <head>

    <title>Test Bulletin</title>

  </head>

  <body>

    <h1>Test Bulletin</h1>

    """



curs.execute('SELECT * FROM messages')

rows = curs.dictfetchall()



toplevel = []

children = {}



for row in rows:

    parent_id = row['reply_to']

    if parent_id is None:

        toplevel.append(row)

    else:

        children.setdefault(parent_id,[]).append(row)



def format(row):

    print '<p><a href="view.cgi?id=%(id)i">%(subject)s</a></p>' % row

    try: kids = children[row['id']]

    except KeyError: pass

    else:

        print '<blockquote>'

        for kid in kids:

            format(kid)

        print '</blockquote>'



print '<p>'



for row in toplevel:

    format(row)



print """

    </p>

    <hr />

    <p><a href="edit.cgi">Post message</a></p>

  </body>

</html>

"""

[/PHP]
[b]Save.cgi[/b[
[PHP]
print 'Content-type: text/html\n'



import cgitb; cgitb.enable()



def quote(string):

    if string:

        return string.replace("'", "\\'")

    else:

        return string



import psycopg

conn = psycopg.connect('dbname=x user=root')

curs = conn.cursor()



import cgi, sys

form = cgi.FieldStorage()



sender = quote(form.getvalue('sender'))

subject = quote(form.getvalue('subject'))

text = quote(form.getvalue('text'))

reply_to = form.getvalue('reply_to')



if not (sender and subject and text):

    print 'Please supply sender, subject, and text'

    sys.exit()



if reply_to is not None:

    query = """

    INSERT INTO messages(reply_to, sender, subject, text)

    VALUES(%i, '%s', '%s', '%s')""" % (int(reply_to), sender, subject, text)

else:

    query = """

    INSERT INTO messages(sender, subject, text)

    VALUES('%s', '%s', '%s')""" % (sender, subject, text)



curs.execute(query)

conn.commit()



print """

<html>

  <head>

    <title>Message Saved</title>

  </head>

  <body>

    <h1>Message Saved</h1>

    <hr />

    <a href='main.cgi'>Back to the main page</a>

  </body>

</html>

"""

[/PHP]
[b]simple_main.cgi[b]
[PHP]
rint 'Content-type: text/html\n'



import cgitb; cgitb.enable()



import psycopg

conn = psycopg.connect('dbname=x user=root')

curs = conn.cursor()



print """

<html>

  <head>

    <title>Test Bulletin Board</title>

  </head>

  <body>

    <h1>Test Bulletin Board</h1>

    """



curs.execute('SELECT * FROM messages')

rows = curs.dictfetchall()



toplevel = []

children = {}



for row in rows:

    parent_id = row['reply_to']

    if parent_id is None:

        toplevel.append(row)

    else:

        children.setdefault(parent_id,[]).append(row)



def format(row):

    print row['subject']

    try: kids = children[row['id']]

    except KeyError: pass

    else:

        print '<blockquote>'

        for kid in kids:

            format(kid)

        print '</blockquote>'



print '<p>'



for row in toplevel:

    format(row)



print """

    </p>

  </body>

</html>

"""

[/PHP]
**view.cgi**
[PHP]
print 'Content-type: text/html\n'



import cgitb; cgitb.enable()



import psycopg

conn = psycopg.connect('dbname=x user=root')

curs = conn.cursor()



import cgi, sys

form = cgi.FieldStorage()

id = form.getvalue('id')



print """

<html>

  <head>

    <title>View Message</title>

  </head>

  <body>

    <h1>View Message</h1>

    """



try: id = int(id)

except:

    print 'Invalid message ID'

    sys.exit()



curs.execute('SELECT * FROM messages WHERE id = %i' % id)

rows = curs.dictfetchall()



if not rows:

    print 'Unknown message ID'

    sys.exit()



row = rows[0]

print """

    <p><b>Subject:</b> %(subject)s<br />

    <b>Sender:</b> %(sender)s<br />

    <pre>%(text)s</pre>

    </p>

    <hr />

    <a href='main.cgi'>Back to the main page</a>

    | <a href="edit.cgi?reply_to=%(id)s">Reply</a>

  </body>

</html>

""" % row

[/PHP]
Any Help will be great.

---

### Post by nanotube on 2008-03-25
if you get source instead of execution, that means you haven't configured your webserver to execute these scripts (also you must chmod them to be executable)
so enable cgi :)

---

### Post by LaRoza on 2008-03-25
Also, you have to use the shebang line.

If apache sees this as .cgi and tries to execute it, how is it supposed to know it is python?

---

### Post by pmasiar on 2008-03-25
[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) has the simplest web application to get you started

---

### Post by PyPhreak on 2008-03-26
Alright thanks guys,I got it figured out..xD..I like your wiki pmasiar

---

