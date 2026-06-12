---
title: "Python timer when web page hangs?"
date: 2007-07-28
forum: Programming Talk
---

### Post by tc101 on 2007-07-28
How do I use a timer in python so that when I am trying to open a web page and it just hangs I can go on in the process after a few seconds?

My code hangs here:

req = urllib2.Request(url)
handle = urllib2.urlopen(req)

with certain urls which also hang in a browser

---

### Post by bbzbryce on 2007-07-29
> **tc101 said:**
> How do I use a timer in python so that when I am trying to open a web page and it just hangs I can go on in the process after a few seconds?

My code hangs here:

req = urllib2.Request(url)
handle = urllib2.urlopen(req)

with certain urls which also hang in a browser

Do something like this:
```
socket.setdefaulttimeout(5)
try:
	req = urllib2.Request(url)
	handle = urllib2.urlopen(req)
except socket.timeout:
	print 'timed out'
```

This will timeout after 5 seconds.

---

### Post by bbzbryce on 2007-07-29
Sorry it should be urllib2.URLError instead of socket.timeout.

```
import urllib2
import socket

socket.setdefaulttimeout(1)

for i in xrange(100):
	try:
		req = urllib2.Request('http://digg.com')
		handle = urllib2.urlopen(req)
	except urllib2.URLError:
		print 'timed out'
	else:
		print i,'sucess'
```

---

### Post by tc101 on 2007-07-29
Thanks for you help bbzbryce.   I was just about to post another question but your second post solved my problem.  

Actually except socket.timeout: got me out of the hang state and continued with the program, but it did not print the message.  I had not established if it exited the whole function or what

```
try:
	req = urllib2.Request(url)
	handle = urllib2.urlopen(req)
except socket.timeout:
	print 'timed out'   #message does not print


try:
	req = urllib2.Request('http://digg.com')
	handle = urllib2.urlopen(req)
except urllib2.URLError:
	print 'timed out'   #message prints fine
```

---

### Post by bbzbryce on 2007-07-29
> **tc101 said:**
> Thanks for you help bbzbryce.   I was just about to post another question but your second post solved my problem.

The first message doesn't print because it's not the proper exception; hence my updated post. If you don't care to handle the exception then just do:

```
try:
	# do something
except:
	pass

```

---

### Post by tc101 on 2007-07-29
OK, now I understand.  It would time out no matter what because of 

socket.setdefaulttimeout(1)

We were just dealing with getting the message to print.  Thanks for your help.

---

### Post by bbzbryce on 2007-07-29
> **tc101 said:**
> OK, now I understand.  It would time out no matter what because of 

socket.setdefaulttimeout(1)

We were just dealing with getting the message to print.  Thanks for your help.

Correct setting the default timeout will throw the urllib2.URLError error. So if you don't have the urlrequest in a try block then your python script will exit and print a stack trace.

---

