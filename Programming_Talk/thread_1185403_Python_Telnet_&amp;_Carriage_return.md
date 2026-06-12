---
title: "Python: Telnet &amp; Carriage return"
date: 2009-06-12
forum: Programming Talk
---

### Post by HavocXphere on 2009-06-12
[Solved]
I've got a string comparison failing in a telnet script and don't know how to fix it.
```

#! /usr/bin/env python

import sys
import telnetlib
import time

HOST = "192.168.1.1"
username = "XXXXXXXXX"
password = "XXXXXXXXX"
response = ""
routertype = "XXXXXXXX ADSL Router"

print "Connecting to router..."
tn = telnetlib.Telnet(HOST)
response = tn.read_until(routertype,1)
if not response == routertype:
	print "Router output unrecognized. Quiting..."
	tn.close()	
	quit()
else:
	print "Router has identified itself. Logging in."
response = tn.read_until("Login: ",1)
tn.write(username + "\n")
response = tn.read_until("Password: ",1)
tn.write(password + "\n")
response = tn.read_until([COLOR="Red"]"/n> "[/COLOR],1)

[COLOR="Red"]if not response == "/n> ":[/COLOR]
	print "Router output unrecognized: *" + response+"*"
	print "Quiting..."
	tn.close()
	quit()
else:
	print "Router has accepted login details."

tn.write("adsl info --stats\n")
print tn.read_until("xxxx",2)

tn.close()
```
There must be some unprintable char there that I can't see. The "/n" is an attempt to fix it...doesn't help.

Terminal output:
```
Havoc@Xphere:~/Documents/Python$ ./Router.py
Connecting to router...
Router has identified itself. Logging in.
Router output unrecognized: [COLOR="Red"]*
> *[/COLOR]
Quiting...
Havoc@Xphere:~/Documents/Python$
```

Otherwise the code works. If I take out the second if-else block then it does actually fetch the router adsl stats as intended.

---

### Post by unutbu on 2009-06-12
Perhaps change '/n' to '\n' ?
If that does not work, change 
```

	print "Router output unrecognized: *" + response+"*"
```

to
```
	print "Router output unrecognized: *" + repr(response)+"*"
```

repr(response) will help you see invisible characters.

---

### Post by HavocXphere on 2009-06-12
> **unutbu said:**
> Perhaps change '/n' to '\n' ?
:redface: Not used to these escape character things. In my defence I did have the slash the right way round at an earlier stage.

> **unutbu said:**
> 
```
	print "Router output unrecognized: *" + repr(response)+"*"
```

repr(response) will help you see invisible characters.
Nice. Useful function and solves the problem at hand.

The hidden chars were: \r\n

Thank you for the help.:guitar:

---

