---
title: "Learning python and don't know why I can use a function"
date: 2007-11-03
forum: Programming Talk
---

### Post by thenetduck on 2007-11-03
Hey I did a little program and wanted to use the upper() function on a string. Not sure why it doesn't work. Here is my code and the error it gives. 

```

""" This program will ask for a username and password and if the the user types in Lock it will require them to enter it, else it doesn't do anything"""
import string
while 1==1:
	userin = raw_input(': ')
	userin = upper(userin)
	while userin == 'LOCK':
		user = raw_input("Enter username: ")
		upass = raw_input("Enter password: ")
		if user != 'user' or upass != 'pass':
			print 'Errt! Wrong! Maybe something different?'
		else:
			userin = 'notLock'

```

and the error

```

: a
Traceback (most recent call last):
  File "exer2.py", line 5, in <module>
    userin = upper(userin)
NameError: name 'upper' is not defined
thenetduck@thenetduck-desktop:~/Programming/Python Tutorial$ 



```

Cant figure... hum....

The Net Duck

Ok I figured it out. I had to do 

import string as s

then put an s.upper(<string>) 

wonder why this wasn't in by default. Hum.....I guess it sorry for the junk post.

---

### Post by ghostdog74 on 2007-11-03
> **thenetduck said:**
> Hey I did a little program and wanted to use the upper() function on a string. Not sure why it doesn't work. Here is my code and the error it gives. 

```

""" This program will ask for a username and password and if the the user types in Lock it will require them to enter it, else it doesn't do anything"""
import string
while 1==1:
	userin = raw_input(': ')
	userin = upper(userin)
	while userin == 'LOCK':
		user = raw_input("Enter username: ")
		upass = raw_input("Enter password: ")
		if user != 'user' or upass != 'pass':
			print 'Errt! Wrong! Maybe something different?'
		else:
			userin = 'notLock'

```

and the error

```

: a
Traceback (most recent call last):
  File "exer2.py", line 5, in <module>
    userin = upper(userin)
NameError: name 'upper' is not defined
thenetduck@thenetduck-desktop:~/Programming/Python Tutorial$ 



```

Cant figure... hum....

The Net Duck

Ok I figured it out. I had to do 

import string as s

then put an s.upper(<string>) 

wonder why this wasn't in by default. Hum.....I guess it sorry for the junk post.
from which references are you learning Python
there's no need for while 1==1, a "while 1" will do.
as for changing the string into uppercase, there's no need to import string

```

while 1:
	userin = raw_input(': ').upper()
       .....

```
I suggest you try the official [tutorial ]("http://docs.python.org/tut/")

---

