---
title: "[Python 2.4] I/O - syntax error with open()"
date: 2011-03-08
forum: Programming Talk
---

### Post by Tompalaz on 2011-03-08
Hi.

I need to generate a HTML file in python 2.4. 
I cant find a good way to do it though.

When I try with open() I get a syntax error. 

Shouldn't this work?
```

MAIL_HTML_MSG="""\
	<html>
	  <head></head>
	  <body>
		<p><b>WARNING!</b>
		   <br>%s on %s is below %d MB
		   <br>Space left: %d MB.
		   <br>Time of Event: %s
		</p>
	  </body>
	</html>
	"""
test = open('/tmp/dump.html','w'):
	test.write(MAIL_HTML_MSG)
        test.close()

```

---

### Post by Tompalaz on 2011-03-08
This seems to work:

```
html_file = open(MAIL_HTML_FILE,'w')
html_file.write(MAIL_HTML_MSG)
html_file.close()

plain_file = open(MAIL_PLAIN_FILE,'w')
plain_file.write(MAIL_PLAIN_MSG)   
plain_file.close()
```

---

### Post by Tony Flury on 2011-03-08
> **Tompalaz said:**
> Hi.

I need to generate a HTML file in python 2.4. 
I cant find a good way to do it though.

When I try with open() I get a syntax error. 

Shouldn't this work?
```

MAIL_HTML_MSG="""\
	<html>
	  <head></head>
	  <body>
		<p><b>WARNING!</b>
		   <br>%s on %s is below %d MB
		   <br>Space left: %d MB.
		   <br>Time of Event: %s
		</p>
	  </body>
	</html>
	"""
test = open('/tmp/dump.html','w'):
	test.write(MAIL_HTML_MSG)
        test.close()

```

I know you have fixed this - but for your eduction the syntax error is that trailing colon after your open function call - the colon is used to identify a sub block - for instance : 

```

if <test>:
   # do something when test is true

```

```

while <test>:
    # Do somethile while test remains true

```

Not sure what you thought the colon would do in your case ?

---

### Post by robots.jpg on 2011-03-08
Could have been thinking of the 'with' block you can use in newer versions of Python:
```

with open('/tmp/dump.html','w') as test:
    test.write(MAIL_HTML_MSG)

```

I don't remember which version added it, but it was definitely after 2.4.

---

