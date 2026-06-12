---
title: "Executing python script for display in gnome panel"
date: 2009-10-29
forum: Programming Talk
---

### Post by exutable on 2009-10-29
Hey guys,

I have a python script that I use for conky(it displays mobile account data).  I want to integrate this into gnome panel so it's displayed at the top.  Is the best way to create an applet?? or just edit the gnome-panel source directly?  Any other suggestions?

Thanks,

Dane

---

### Post by johnl on 2009-10-29
The best way for sure is to create an applet.  

[this page](http://my.opera.com/BasicWolf/blog/2009/02/25/beginners-guide-to-creating-a-gnome-applet-with-python-part-i) has a pretty up-to-date (the only other tutorial I found was from 2004) tutorial that should help you.

---

### Post by exutable on 2009-10-31
Ahh thanks,

Got it working but now I have the weirdest issue.

This code works perfectly:

```
#!/usr/bin/env python
import urllib
import urllib2
import sys
import cookielib
import hashlib
import gtk
import pygtk
import gnomeapplet
pygtk.require('2.0')

from BeautifulSoup import BeautifulSoup

#Accept cookies to browse telmore website
cookieJar = cookielib.LWPCookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))

#Add headers
opener.addheaders = [('User-agent', "Mozilla/5.0")]

#Accept arguments for username and password
username = sys.argv[1]
password = sys.argv[2]

#Url requests, first page is login, second is a frame of the login page
url = "https://www.telmore.dk/t2/j_security_check"
url2 = "https://www.telmore.dk/t2/mytelmore/index.do"

#Fill the forms with the username and password arguments
form = { "j_username" : username,
         "j_password" : password }

#Encode the form and create request		 
encodedForm = urllib.urlencode(form)
request = urllib2.Request(url, encodedForm)
page = opener.open(request)

#Request the second page
request = urllib2.Request(url2)
page = opener.open(request)
contents = page.read()

#Beatiful soup to parse the html and sort out the span tag with class saldo
soup = BeautifulSoup(contents)
saldospan = soup.findAll('span')
saldo = saldospan[0].contents[0].strip()

print saldo

def applet_factory(gnome_applet, iid):   
   label = gtk.Label("{0} kr.".format(saldo))
   gnome_applet.add(label)
   gnome_applet.show_all()
   print('Factory started')
   return True
            
if __name__ == '__main__':   # testing for execution
   print('Starting factory')
   gnomeapplet.bonobo_factory('OAFIID:TelmoreApplet_Factory', 
                              gnomeapplet.Applet.__gtype__, 
                              'Telmore Applet', '0.1', 
                              applet_factory)
```

yet if I read from a file and then print... it doesn't:
```
#!/usr/bin/env python
import urllib
import urllib2
import sys
import cookielib
import hashlib
import gtk
import pygtk
import gnomeapplet
pygtk.require('2.0')

f = open('saldo.txt', 'r')
saldo = f.readline().strip()
f.close()

print saldo

def applet_factory(gnome_applet, iid):   
   label = gtk.Label("{0} kr.".format(saldo))
   gnome_applet.add(label)
   gnome_applet.show_all()
   print('Factory started')
   return True
            
if __name__ == '__main__':   # testing for execution
   print('Starting factory')
   gnomeapplet.bonobo_factory('OAFIID:TelmoreApplet_Factory', 
                              gnomeapplet.Applet.__gtype__, 
                              'Telmore Applet', '0.1', 
                              applet_factory)
```

---

