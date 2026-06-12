---
title: "Python Cookie help"
date: 2009-06-27
forum: Programming Talk
---

### Post by matmatmat on 2009-06-27
I have the following files:
```

# add.py
#!/usr/bin/env python
import os
import Cookie
import hashlib
import MySQLdb
import cgi
import cgitb; cgitb.enable()
def showform():
	reshtml = '''Content-Type: text/html\n
	<html>
	<body>
	<form action='add.py' method='post'>
	Name: <input type=text name=name size = 15><br>
	URL : <input type=text name=url size=30><br>
	<input type=submit value="Add"></form>
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
        name = form['name'].value
        url = form['url'].value
        cookie = Cookie.SimpleCookie()
        string_cookie = os.environ.get('HTTP_COOKIE')
        if string_cookie:
                user = cookie['u'].value
        else:
                user = "dad"
        cursor.execute("insert into bookmarks values ('%s', '%s', '%s')" % (user, name, url))
        print reshtml % ("")

form = cgi.FieldStorage()
if not form.has_key('url'):
	showform()
else:
	main()

```

```

#!/usr/bin/env python
import os
import Cookie
import hashlib
import MySQLdb
import cgi
import cgitb; cgitb.enable()
def showform():
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
                cookie = Cookie.SimpleCookie()
                string_cookie = os.environ.get('HTTP_COOKIE')
                if not string_cookie:
                        cookie['u'] = who
                else:
                        cookie['u'] = who
                print cookie
                cursor.execute("select name, url from bookmarks where user='%s'" % (who))
                ro = cursor.fetchall()
                st = []
                for row in ro:
                        st.append([row[0], row[1]])
		blah = "<a href='add.py'>add bookmark</a>\n"
		for s in st:
			for a in s:
				blah += a + "\t\t"
			blah += "\n"
                print reshtml % (blah)

form = cgi.FieldStorage()
if not form.has_key('person'):
	showform()
else:
	main()

```
in add.py it gives a key error at the cookie bit, why?

---

