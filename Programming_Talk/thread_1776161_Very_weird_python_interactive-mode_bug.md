---
title: "Very weird python interactive-mode bug"
date: 2011-06-05
forum: Programming Talk
---

### Post by adempewolff on 2011-06-05
[SIZE="4"]Executive Summary:[/SIZE]

(I am using Python 2.7.1+)

I am encountering a weird bug with the interactive mode of the python interpreter that I cannot get to go away.  To summarize, while in interactive mode, three times, commands ('print data' the two times,  "re.search('Content-Type: \S+\n\n.*$', page)" the most recent time) resulted in the unexpected behaviour of executing the last program I ran in non-interactive mode (ie. 'python socket3.py' from the terminal).

```
austin@austin-Latitude-D630:~$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> print data
Enter a url: 
Invalid url
Enter a url: 
Invalid url
Enter a url: 
Invalid url
Enter a url: exit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'data' is not defined 
```

```
 austin@austin-Latitude-D630:~$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> print data
Enter a url: exit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'data' is not defined 
```

```
>>> re.search('Content-Type: \S+\n\n.*$', page)
Enter a url: done
Invalid url: no tld
Enter a url: www.py4inf.com/code/romeo-full.txt
Debug: host is 'www.py4inf.com'
Debug: url is 'http://www.py4inf.com/code/romeo-full.txt'
^C
Page not found
Enter a url: 
Invalid url
Enter a url: exit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 're' is not defined
```

[SIZE="4"]How I encountered the bug:[/SIZE]

While I don't expect corrections for my python code (not that they aren't welcome, I just figure people have better things to do than correct my sloppy code), describing the program I was writing might help to reproduce the problem.

The program I was debugging (and that seems to be being called unexpectedly in interactive mode is:

```
import socket
import re

while True:
	url = raw_input('Enter a url: ').lower()
	if url == 'exit' : exit()
	elif url.startswith('https://'):
		print 'SSL not supported'
		continue
	elif url.find('/') == -1 : url = url + '/'
	host = re.findall('^[http://]*(\S+?.[a-z]+?)/\S*', url)
	if len(host) == 0 :
		print 'Invalid url'
		continue
	lst = host[0].split('.')
	tld = lst[len(lst) - 1]
	if len(lst) == 1:
		print 'Invalid url: no tld'
		continue
	elif not 1 < len(tld) <= 3:
		print 'Invalid url: invalid tld format'
		continue
	print "Debug: host is '{}'".format(host[0])
	mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	try : mysock.connect((host[0], 80))
	except:
		print 'Server not found'
		continue
	if url.startswith('www.') : url = 'http://' + url
	elif url.find('/') == -1 : url = url + '/'
	print "Debug: url is '{}'".format(url)
	mysock.send('GET {} HTTP/1.0\n\n'.format(url))
	break

page = str()
toprint = str()
p = False

while True:
	data = mysock.recv(512) 
	if ( len(data) < 1 ) : break
	page = page + data
	print repr(data) ## I just put these lines in for
	exit()           ## debugging as described below
	if re.search('Content-Type: \S+\n\n.*$', page) :
		print 'found head'
		remainder = re.findall('Content-Type: \S+\n\n(.*$)', page)[0]
		toprint = toprint + remainder
		p = True
	elif p == True:
		if 3000 - len(toprint) <= len(data) :
			toprint = toprint + data
		elif 3000 - len(toprint) > len(data) :
			remainder = len(3000 - len(toprint))
			toprint = toprint + data[0 : remainder - 1]
			prnt = False
print toprint
print page
print 'Length: {} out of {} total characters'.format(len(toprint),len(page))

mysock.close()
```

When I encountered the problem, I was trying to debug the regular expression that searches for the beginning of the body of the document (I didn't want to print the headers).

```
	if re.search('Content-Type: \S+\n\n.*$', page) : 
```

To do so I added two lines in to print off the first 512 chars, so I could use them as a string in interactive mode for debugging my regular expression.

I made a mistake here in that I just printed these characters to stdout unmodified and copied them--I should have printed the repr() of them instead.

I then went into interactive mode and typed,
>>>data = '
and then hit paste--stupid--which, as might be expected, resulted in craziness as all the line breaks were parsed as returns and caused lots of problems.

I reopened python and typed
>>>print data
to see what, if anything was saved to the variable.  This is when the first occurence of this bug occurred.  

```
>>> print data
Enter a url: 
Invalid url
Enter a url: 
Invalid url
Enter a url: 
Invalid url
Enter a url: exit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'data' is not defined
```

after more confusion, because I didn't realize python exited

```
austin@austin-Latitude-D630:~$ print repr(data)
bash: syntax error near unexpected token `('
austin@austin-Latitude-D630:~$ data
No command 'data' found, did you mean:
 Command 'dat' from package 'liballegro4.2-dev' (universe)
 Command 'date' from package 'coreutils' (main)
data: command not found
austin@austin-Latitude-D630:~$ print data
Warning: unknown mime-type for "data" -- using "application/octet-stream"
Error: no such file "data"
```

I reopened python and tried the command again, with the same results.
```
austin@austin-Latitude-D630:~$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> print data
Enter a url: exit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'data' is not defined
```

after spending a little while scratching my head I overwrote the variable 'data' which seemed to resolve the problem.
```
>>> b = 'd'
>>> print b
d
>>> data ='abf'
>>> print data
abf
>>> 
```

I then corrected my earlier mistake by editing my program and changing the debug line 'print data' to 'print repr(data)'

I then ran the program again and copied the repr()'ified output into the variable data in interactive mode.
```
austin@austin-Latitude-D630:~$ python socket3.py
Enter a url: www.py4inf.com/code/romeo-full.txt
Debug: host is 'www.py4inf.com'
Debug: url is 'http://www.py4inf.com/code/romeo-full.txt'
'HTTP/1.1 200 OK\r\nDate: Sun, 05 Jun 2011 19:56:24 GMT\r\nServer: Apache\r\nLast-Modified: Fri, 05 Nov 2010 03:37:37 GMT\r\nETag: "180dc16e-22a0-4cd37c01"\r\nAccept-Ranges: bytes\r\nContent-Length: 8864\r\nConnection: close\r\nContent-Type: text/plain\r\n\r\nRomeo and Juliet\nAct 2, Scene 2 \n\nSCENE II. Capulet\'s orchard.\n\nEnter ROMEO\n\nROMEO\n\nHe jests at scars that never felt a wound.\nJULIET appears above at a window\n\nBut, soft! what light through yonder window breaks?\nIt is the east, and Juliet is the sun.\nArise, fair sun, and '
austin@austin-Latitude-D630:~$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> data = 'HTTP/1.1 200 OK\r\nDate: Sun, 05 Jun 2011 19:56:24 GMT\r\nServer: Apache\r\nLast-Modified: Fri, 05 Nov 2010 03:37:37 GMT\r\nETag: "180dc16e-22a0-4cd37c01"\r\nAccept-Ranges: bytes\r\nContent-Length: 8864\r\nConnection: close\r\nContent-Type: text/plain\r\n\r\nRomeo and Juliet\nAct 2, Scene 2 \n\nSCENE II. Capulet\'s orchard.\n\nEnter ROMEO\n\nROMEO\n\nHe jests at scars that never felt a wound.\nJULIET appears above at a window\n\nBut, soft! what light through yonder window breaks?\nIt is the east, and Juliet is the sun.\nArise, fair sun, and '
>>> len(data)
512
```

I then proceded trying to debug my regular expression (thinking the bug was behind me), by replicating the first iteration of a loop in my program, parsing the first 512 char of a webpage, now contained in data.

part of loop I was trying to debug:
```
while True:
	data = mysock.recv(512) 
	if ( len(data) < 1 ) : break
	page = page + data
	print repr(data)
	exit()
	if re.search('Content-Type: \S+\n\n.*$', page) :
		print 'found head'
		remainder = re.findall('Content-Type: \S+\n\n(.*$)', page)[0]
		toprint = toprint + remainder
		p = True
```

what I entered into interactive-mode emulating this loop:
```
>>> page = str()
>>> page = page + data
>>> re.search('Content-Type: \S+\n\n.*$', page)
Enter a url: done
Invalid url: no tld
Enter a url: www.py4inf.com/code/romeo-full.txt
Debug: host is 'www.py4inf.com'
Debug: url is 'http://www.py4inf.com/code/romeo-full.txt'
^C
Page not found
Enter a url: 
Invalid url
Enter a url: exit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 're' is not defined
```

As you can see the bug came back.  And I am at a lose at how to stop it.  It seems like maybe there is an artifact of my program in the memory the interpreter is using or something.  However, each time the bug showed up, I had closed interactive-mode and restarted it--which I thought cleared all the memory/variables/whatnot python had been using.

Any advice would be appreciated.
[SIZE="4"]
To reproduce the bug, try:[/SIZE]

1. saving and running this program (enter 'www.py4inf.com/code/romeo-full.txt' when prompted):
(I should probably put the obvious disclaimer here that one should only run code found on the forums when they understand what it does.  so if you ran across this thread and don't know python, you shouldn't get in the habit of running code if you don't know what it does.)
```
import socket
import re

while True:
	url = raw_input('Enter a url: ').lower()
	if url == 'exit' : exit()
	elif url.startswith('https://'):
		print 'SSL not supported'
		continue
	elif url.find('/') == -1 : url = url + '/'
	host = re.findall('^[http://]*(\S+?.[a-z]+?)/\S*', url)
	if len(host) == 0 :
		print 'Invalid url'
		continue
	lst = host[0].split('.')
	tld = lst[len(lst) - 1]
	if len(lst) == 1:
		print 'Invalid url: no tld'
		continue
	elif not 1 < len(tld) <= 3:
		print 'Invalid url: invalid tld format'
		continue
	print "Debug: host is '{}'".format(host[0])
	mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	try : mysock.connect((host[0], 80))
	except:
		print 'Server not found'
		continue
	if url.startswith('www.') : url = 'http://' + url
	elif url.find('/') == -1 : url = url + '/'
	print "Debug: url is '{}'".format(url)
	mysock.send('GET {} HTTP/1.0\n\n'.format(url))
	break

page = str()
toprint = str()
p = False

while True:
	data = mysock.recv(512) 
	if ( len(data) < 1 ) : break
	page = page + data
	print data
	exit()
	if re.search('Content-Type: \S+\n\n.*$', page) :
		print 'found head'
		remainder = re.findall('Content-Type: \S+\n\n(.*$)', page)[0]
		toprint = toprint + remainder
		p = True
	elif p == True:
		if 3000 - len(toprint) <= len(data) :
			toprint = toprint + data
		elif 3000 - len(toprint) > len(data) :
			remainder = len(3000 - len(toprint))
			toprint = toprint + data[0 : remainder - 1]
			prnt = False
print toprint
print page
print 'Length: {} out of {} total characters'.format(len(toprint),len(page))

mysock.close()
```

2. copying and pasting the 512 chars printed to stdout (which I've provided here as well):

```
HTTP/1.1 200 OK
Date: Sun, 05 Jun 2011 20:49:40 GMT
Server: Apache
Last-Modified: Fri, 05 Nov 2010 03:37:37 GMT
ETag: "180dc16e-22a0-4cd37c01"
Accept-Ranges: bytes
Content-Length: 8864
Connection: close
Content-Type: text/plain

Romeo and Juliet
Act 2, Scene 2 

SCENE II. Capulet's orchard.

Enter ROMEO

ROMEO

He jests at scars that never felt a wound.
JULIET appears above at a window

But, soft! what light through yonder window breaks?
It is the east, and Juliet is the sun.
Arise, fair sun, and 
```

3. opening python interactive mode:

```
$python
```

4. typing "data = '"

```
>>>data = '
```

5. Pasting the clipboard (causing a number of errors)

6. reopening python interactive-mode

7. and typing 'print data':

```
>>>print data
```

This should cause the prompt 'Enter a url: ' to appear.  (typing 'exit' will kill the program)

---

### Post by adempewolff on 2011-06-05
So with a little more experimenting I've discovered that anytime an undefined variable is called, it executes the program.

For example:

>>>print asdf

would do it, but

>>>asdf = 123
>>>print asdf

would not.


still trying to get this silliness to go away so I can go back to programming!

---

