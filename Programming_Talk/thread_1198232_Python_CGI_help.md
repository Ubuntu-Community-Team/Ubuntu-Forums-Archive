---
title: "Python CGI help"
date: 2009-06-27
forum: Programming Talk
---

### Post by matmatmat on 2009-06-27
Is there a way to keep field names out of the url, eg
```

#!/usr/bin/env python
import hashlib
import MySQLdb
import cgi
import cgitb; cgitb.enable()
def showform():
	reshtml = '''Content-Type: text/html\n
	<html>
	<body>
	<a href="register.py">Not a member? </a>
	<form action='login.py'>
	Username: <input type=text name=person value="New User" size = 15><br>
	Password: <input type=password name=pass value="" size=15><br>
	<input type=submit value="Login"></form>
	</body>
	</html>
	'''
	print reshtml

def main():
        conn = MySQLdb.connect(host="localhost", user="root", passwd="", db="test")
        reshtml = '''Content-Type: text/html\n
        <html><body>
        %s
        </body>
        </html>
        '''
        cursor = conn.cursor ()
        form = cgi.FieldStorage()
        who = form['person'].value
        passw = form['pass'].value
        m = hashlib.md5()
        m.update(passw)
        cursor.execute("select * from pass where user='%s' and passwrd='%s'" % (who, m.digest()))
        if cursor.rowcount != 1:
                print reshtml % ("Invalid username or password")
        else:
                cursor.execute("select name, url from bookmarks where user='%s'" % (who))
                ro = cursor.fetchall()
                st = []
                for row in ro:
                        st.append([row[0], row[1]])
                print reshtml % (st)

form = cgi.FieldStorage()
if not form.has_key('person'):
	showform()
else:
	main()

``` 
and the url not being:
```

http://localhost:8000/cgi-bin/login.py?person=user&pass=user

```
?

---

### Post by -grubby on 2009-06-27
Yes. The variables you see in the URL are GET variables, and the variables you don't see are called POST variables. In your HTML, use the following code:

[html]
<form action="something" method="post">
[/html]

Note the method.

---

### Post by matmatmat on 2009-06-27
I have this
```

	reshtml = '''Content-Type: text/html\n
	<html>
	<body>
	<a href="register.py">Not a member? </a>
	<form action='login.py' method="post">
	Username: <input type=text name=person value="New User" size = 15><br>
	Password: <input type=password name=pass value="" size=15><br>
	<input type=submit value="Login"></form>
	</body>
	</html>
	'''

```
but it doesn't connect

---

### Post by matmatmat on 2009-06-27
It exits with a 
```
0x100
```
error

I'm running with:
```

python -m CGIHTTPServer

```

---

### Post by smartbei on 2009-06-27
Are you sure the error is in that segment? That looks fine...

---

