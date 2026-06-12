---
title: "Python: only part of a txt file is saved"
date: 2009-03-13
forum: Programming Talk
---

### Post by blairm on 2009-03-13
Hi,

Trying to download two rss feeds as text files before emailing them; the first (stuff.co.nz/rss/national) works fine, but the second (stuff.co.nz/rss) is only picking up the first of five items. Have I missed some vital joining piece of code?
I'm assuming that if a section of code does the job well for one feed from a site, it should wok for another on the same site as well - so the problem is probably me.
Still new to programming so have included pretty much the whole script to date for fear of leaving out something relevant; apologies for that.

Blair 

PS: Aware the email is sending a different file at present; figured I'd turn my mind to the email section once I established I had two full lists to email! 

```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom
#import hashlib
import os
#import time


#The url of the feed
address = 'http://www.stuff.co.nz/rss/national'

#Our actual xml document
f = open('appendtest.txt',  'w')

document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))
    
    #The url of the feed
addresstwo = 'http://www.stuff.co.nz/rss/'
#Our actual xml document
f = open('appendtesttop.txt',  'w')
document = xml.dom.minidom.parse(urllib.urlopen(addresstwo))

for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))


f.close()

import smtplib

# from http://stackoverflow.com/questions/399129/failing-to-send-email-with-the-python-example
FROMADDR = "my.name@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "mypassword"
TOADDRS  = ["my.name@xtra.co.nz",  "my.name@work.co.nz"]
SUBJECT  = "Top/National combined test alert"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += open('alerttest.txt', 'r').read()

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()

  

```

---

### Post by croto on 2009-03-14
Hey man,

the problem with the second feed is that the site is giving just 5 items in their feed. You can check it yourself by opening the feed with firefox (just type in the url of the feed in the address bar), it will format it nice for you. If you want to see more, just check the source of that page (ctrl-u).

---

### Post by blairm on 2009-03-15
Sorry, I don't understand... I know the second feed has only five items. Why is it I can only get the first of those five?

Blair

---

### Post by croto on 2009-03-15
I'm sorry, it was my fault. I hadn't read your question properly.

The only problem I see is that, in the code that process the second feed, the print statement is not indented as the inner part of the loop. So it's executing the loop and then the print statement, printing out only the last item.

---

### Post by blairm on 2009-03-15
Thanks for that, all sorted. Has been a good lesson - you can read all you like about the importance of indents in python, but it's no substitute for learning by experience! 

Blair

---

