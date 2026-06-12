---
title: "Python CGI error"
date: 2009-06-24
forum: Programming Talk
---

### Post by matmatmat on 2009-06-24
I have this html:
```

<html>
<body>
<form action='super.py'>
<input type=text name=person value="New User" size = 15>
<input type=submit></form>
</body>
</html>

```
& this python script:
```

<html>
<body>
<form action='super.py'>
<input type=text name=person value="New User" size = 15>
<input type=submit></form>
</body>
</html>
matio@matio-desktop:~$ cat /var/www/py/super.py 
#!/usr/bin/env python

import cgi

rehtml = '''Content-Type: text/html\n
<html><body>
Your name is %s
</body>
</html>
'''
form = cgi.FieldStorage()
who = form['person'].value
print reshtml % (who)

```
when i click submit:
```

MOD_PYTHON ERROR

ProcessId:      14109
Interpreter:    '127.0.1.1'

ServerName:     '127.0.1.1'
DocumentRoot:   '/var/www'

URI:            '/py/super.py'
Location:       None
Directory:      '/var/www/py/'
Filename:       '/var/www/py/super.py'
PathInfo:       ''

Phase:          'PythonHandler'
Handler:        'hello'

Traceback (most recent call last):

  File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch
    default=default_handler, arg=req, silent=hlist.silent)

  File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1202, in _process_target
    module = import_module(module_name, path=path)

  File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 304, in import_module
    return __import__(module_name, {}, {}, ['*'])

ImportError: No module named hello


```
whats wrong?

---

### Post by matmatmat on 2009-06-25
bump

---

### Post by matmatmat on 2009-06-25
Now fixed the "hello" problem by braking something else, here is my /etc/apache2/sites-enabled/000-default:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On

	</Directory>
        <Directory /var/www/py>
                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug Off
        </Directory>


	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```
when I try to go to a .py file it gives a 404

---

### Post by Can+~ on 2009-06-25
Well, I'm a Python user, but never actually tried python and apache together (django comes with it's own server).

So I'm gonna skip the code and say: make sure apache2 has permissions on the files, leave them in such that apache can read the script but nothing else, like:

```
   owner      group
yourusername www-data  rw-r-----
```

(www-data is a special group for apache)

*edit: Found a tutorial:
[http://modpython.org/live/current/doc-html/](http://modpython.org/live/current/doc-html/)

---

### Post by matmatmat on 2009-06-26
How do I change the permission

---

### Post by stevescripts on 2009-06-26
either through cpanel (or whatever your web provider uses), or ssh

Steve

---

### Post by matmatmat on 2009-06-26
it's local

---

### Post by stevescripts on 2009-06-26
[http://www.hostingmanual.net/other/permissions.shtml](http://www.hostingmanual.net/other/permissions.shtml)

Steve

---

### Post by smartbei on 2009-06-26
Since you are running with CGI and not mod_py (if I understand you correctly), then you actually need execution priveleges as well.

EDIT: I see you are using mod_python. Never Mind then.

---

### Post by matmatmat on 2009-06-26
Nothing seems to be working so I tried:
```

python -m CGIHTTPServer

```
& it worked, but can u use it with databases?

---

