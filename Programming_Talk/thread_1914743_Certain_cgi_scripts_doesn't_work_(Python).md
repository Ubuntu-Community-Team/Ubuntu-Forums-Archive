---
title: "Certain cgi scripts doesn't work (Python)"
date: 2012-01-25
forum: Programming Talk
---

### Post by Chanpa on 2012-01-25
I'm currently in the process of learning python and currently im doing databases/web code. And I ran into a problem when trying to run a certain script.
This is my webserver.py:
```
import os, sys
from http.server import HTTPServer, CGIHTTPRequestHandler

webdir = '.'	# where your html files and cgi-bin directory lives
port = 80

os.chdir(webdir)		#run in HTML root dir
srvraddr = ("", port)	#my hostname, portnumber
srvrobj = HTTPServer(srvraddr, CGIHTTPRequestHandler)
srvrobj.serve_forever()
```
I managed to get the first script I made to run, cgi101.py:
```
#!/usr/bin/env python3

import cgi

form = cgi.FieldStorage()					# parse form data
print('Content-type: text/html\n')
print('<title>Reply Page</title>')
if not 'user' in form:
	print('<h1>Who are you?</h1>')
else:
	print('<h1>Hello <i>%s</i>' % cgi.escape(form['user'].value))
```
But when I try to run another script, peoplecgi.py:
```
#!/usr/bin/env python3
"""
Implement a web-based interface for viewing and updating class instances
stored in a shelve; the shelve lives on server (same machine if localhost)
"""
import cgi, shelve, sys, os			# cgi.test() dumps inputs

shelvename = 'class-shelve'			# shelve files are in cwd
fieldnames = ('name', 'age', 'job', 'pay')

form = cgi.FieldStorage() 			# parse form data
print('Content-type: text/html')		# hdr, blank line is in replyhtml
sys.path.insert(0, os.getcwd())			# so this and pickler find person

# main html template
replyhtml = """
<html>
<title>People Input Form</title>
<body>
<form method=POST action="peoplecgi.py">
	<table>
	<tr><th>key<td><input type=text name=key value="%(key)s">
	$ROWS$
	</table>
	<p>
	<input type=submit value="Fetch", name=action>
	<input type=submit value="Update", name=action>
	</form>
	</body></html>
"""

# insert html for data rows at $ROWS$
rowhtml = '<tr><th>%s<td><input type=text name=%s value="%%(%s)s">\n'
rowshtml = ''
for fieldname in fieldnames:
	rowshtml += (rowhtml % ((fieldname,) * 3))
replyhtml = replyhtml.replace('$ROWS$', rowshtml)

def htmlize(adict):
	new = adict.copy()
	for field in fieldnames: # values may have &, >, etc.
		value = new[field] # display as code: quoted
		new[field] = cgi.escape(repr(value)) # html-escape special chars
	return new
def fetchRecord(db, form):
	try:
		key = form['key'].value
		record = db[key]
		fields = record.__dict__ # use attribute dict
		fields['key'] = key # to fill reply string
	except:
		fields = dict.fromkeys(fieldnames, '?')
		fields['key'] = 'Missing or invalid key!'
	return fields
def updateRecord(db, form):
	if not 'key' in form:
		fields = dict.fromkeys(fieldnames, '?')
		fields['key'] = 'Missing key input!'
	else:
		key = form['key'].value
		if key in db:
			record = db[key] # update existing record
		else:
			from person import Person # make/store new one for key
			record = Person(name='?', age='?') # eval: strings must be quoted
		for field in fieldnames:
			setattr(record, field, eval(form[field].value))
		db[key] = record
		fields = record.__dict__
		fields['key'] = key
	return fields

db = shelve.open(shelvename)	
action = form['action'].value if 'action' in form else None
if action == 'Fetch':
	fields = fetchRecord(db, form)
elif action == 'Update':
	fields = updateRecord(db, form)
else:
	fields = dict.fromkeys(fieldnames, '?') # bad submit button value
	fields['key'] = 'Missing or invalid action!'
db.close()
print(replyhtml % htmlize(fields)) # fill reply from dict
```
I get the following error:
```
localhost.localdomain - - [25/Jan/2012 05:45:21] "POST /cgi-bin/peoplecgi.py HTTP/1.1" 200 -
Traceback (most recent call last):
  File "/home/johan/Desktop/Python/cgi-bin/peoplecgi.py", line 73, in <module>
    db = shelve.open(shelvename)	
  File "/usr/lib/python3.2/shelve.py", line 232, in open
    return DbfilenameShelf(filename, flag, protocol, writeback)
  File "/usr/lib/python3.2/shelve.py", line 216, in __init__
    Shelf.__init__(self, dbm.open(filename, flag), protocol, writeback)
  File "/usr/lib/python3.2/dbm/__init__.py", line 89, in open
    return mod.open(file, flag, mode)
_dbm.error: [Errno 13] Permission denied
localhost.localdomain - - [25/Jan/2012 06:31:04] CGI script exit status 0x100

```
Since it says permission denied I'm guessing it has something to with that but I'm not very educated in the unix ways. I checked another thread and there they suggested doing *sudo chmod a+x* on the script and I did but it didn't change anything.

At first I though I had made a typo so I copied the script from my e-book (O'Reilly, programming Python fourth edition) and I get the same error.

If someone can help me figure out what's wrong that would be awesome!

Thanks,
Chanpa

---

### Post by ofnuts on 2012-01-25
For me that just means that you have not got the access rights on the file used to hold the shelf. Check that you have access to it, or change that to be a file you can read/write in a directory on which you have rights?

"chmod +x" on the script makes it executable, and since you get such an error you are executing it so it already is :)

---

### Post by Chanpa on 2012-01-25
I went through every file involved and changed all permissions to Read and Write and it worked. Thought I had done that. Thank you!

---

