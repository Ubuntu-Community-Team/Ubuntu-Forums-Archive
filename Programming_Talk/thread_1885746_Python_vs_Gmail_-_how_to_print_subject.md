---
title: "Python vs Gmail - how to print subject"
date: 2011-11-23
forum: Programming Talk
---

### Post by layr on 2011-11-23
I'm using this python with conky to check email count.
How could the last mail (new or old) subject be printed out?

```
#!/usr/bin/python
import urllib2 
import base64
import os

#check internet connection:
try:
	urllib2.urlopen("http://www.google.com")
except urllib2.URLError:
	g = open("/home/laur/.conky/conky_connection_down.dat", "w")
   	g.write( "This file indicates there is no active Internet connection." )
	g.close()
	if (os.path.exists('/home/laur/.conky/gmail_count.dat')):
		os.remove('/home/laur/.conky/gmail_count.dat')
else:
	# Enter your username and password below within double quotes
	# eg. username="username" and password="password"
	# Install base64 for simple password encryption: "sudo apt-get install cl-base64"
	# To get the encrypted version-> "print base64.b64encode("yourpasswd")"
	domain="mail.google.com"
	username="USERNAME"
	password=base64.b64decode("ENCODED_PASSWD")
	com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

	temp=os.popen(com)
	msg=temp.read()
	index=msg.find("<fullcount>")
	index2=msg.find("</fullcount>")
	fc=int(msg[index+11:index2])
	
	if fc==0:
		if (os.path.exists('/home/laur/.conky/gmail_count.dat')):
			os.remove('/home/laur/.conky/gmail_count.dat')
		if (os.path.exists('/home/laur/.conky/conky_connection_down.dat')):
			os.remove('/home/laur/.conky/conky_connection_down.dat')
	else:
	        f = open("/home/laur/.conky/gmail_count.dat", "w")
   	        f.write( str(fc) )
		f.close()
		if (os.path.exists('/home/laur/.conky/conky_connection_down.dat')):
			os.remove('/home/laur/.conky/conky_connection_down.dat')
```

---

### Post by MadCow108 on 2011-11-24
why the fragile scraping?

ever heard of imap?

```
import getpass, imaplib

m = imaplib.IMAP4_SSL("imap.googlemail.com","993")
m.login(getpass.getuser(), getpass.getpass())
m.select("INBOX", readonly=True)
print m.search(None, '(UNSEEN)')
# fetch message 1832
#m.fetch(1832, '(RFC822)')
m.close()
m.logout()
```

---

