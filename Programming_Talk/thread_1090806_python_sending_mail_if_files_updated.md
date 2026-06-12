---
title: "python: sending mail if files updated"
date: 2009-03-08
forum: Programming Talk
---

### Post by blairm on 2009-03-08
Hi,

After four pretty intense days and with the help of the forum I've managed to piece together something a small python script that collects an rss feed and emails it to me at work; have also set it to run as a Cron task every hour. Been an educational few days.
Am wondering, however, whether I can alter the code so only updated lists of headlines are emailed.

From what I've read filecomp would probably come into it,or possibly md%; file size is no good, as the emails are all the same size. 
In the context of this script, thinking I would need to have the latest feed download put into a file. 
It would be compared with the previous feed (stored in the alerttest,txt file), running along the lines of:

- if latest downland is equal to previous one overwrite alerttest.txt and do not send email.
- if latest download is not equal to previous one overwrite alerttest.txt and send email with updated contents of alerttest.txt. 

Am I overcomplicating things here? I have an unfortunate tendency to miss the simple answers sometimes.:(

Cheers,

Blair

PS: Code, if required, is below:

```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom

#The url of the feed
address = 'http://www.stuff.co.nz/rss/'

#Our actual xml document
f = open('alerttest.txt',  'w')

document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '''<a href="%s">%s</a> (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))

f.close()
import smtplib

# from http://stackoverflow.com/questions/399129/failing-to-send-email-with-the-python-example
FROMADDR = "orpheus.alert@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "mypassword"
TOADDRS  = ["my.name@xtra.co.nz"]
SUBJECT  = "Test alert"

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

### Post by geirha on 2009-03-08
Write the data to a different file (Add a ".tmp" to the for instance, or use the tempfile module), then compare the checksum of the real file and the tmp file. If they match, remove the tempfile and exit, if they don't match, overwrite the real file with the .tmp file (os.rename) and send the mail.

```

import hashlib, os
# ...

f= open('alerttest.txt.tmp','w')
# print the data to the file as before
f.close()

orig_md5= hashlib.md5(file('alerttest.txt').read())
new_md5=  hashlib.md5(file('alerttest.txt.tmp').read())

if orig_md5.digest() == new_md5.digest():
    os.remove('alerttest.txt.tmp')
    # exit or something ...
else:
    os.rename('alerttest.txt.tmp','alerttest.txt')
    # send mail ...

```

---

### Post by blairm on 2009-03-09
That seems to have done the trick. Thanks for your help.


Blair

---

