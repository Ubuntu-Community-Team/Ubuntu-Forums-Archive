---
title: "re.sub problems"
date: 2009-04-18
forum: Programming Talk
---

### Post by blairm on 2009-04-18
Solved just a few minutes after posting: incorrect file name used. More than a little embarrassed...

Blair

Hi,

Have written something to pick up rss feeds and send emails when they feeds are updated; the basics work fine but having a lot of trouble getting it to insert newline characters. The code is here:

```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom
import hashlib
import os
import re
#import time


#The url of the feed
address = 'http://www.stuff.co.nz/rss/'

#Our actual xml document
f = open('appendtest.txt.tmp',  'w')

document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))
    
    #The url of the feed
addresstwo = 'http://www.stuff.co.nz/rss/national'
#Our actual xml document
f = open('appendtest.txt.tmp',  'a')
print>>f, "NATIONAL STORIES"
document = xml.dom.minidom.parse(urllib.urlopen(addresstwo))

for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))

 

f.close()

fh = open('appendtest.txt.tmp','r')
stuff = fh.read()
fh.close()

new_stuff = re.sub(r'\(', r')\n\n\(',stuff)
fh = open('newstuff.txt','w')
fh.write(new_stuff)
fh.close()

import md5
orig_md5= hashlib.md5(file('newstuff.txt').read())
new_md5= hashlib.md5(file('appendtest.txt.tmp').read())
if orig_md5.digest() == new_md5.digest():
    os.remove('appendtest.txt.tmp')
    sys.exit()
else:
    os.rename('appendtest.txt.tmp',  'newstuff.txt')

import smtplib

 #from http://stackoverflow.com/questions/399129/failing-to-send-email-with-the-python-example
FROMADDR = "my_address@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "my_password"
TOADDRS  = ["email one",  "email two"]
SUBJECT  = "Top/National combined test alert"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += open('newstuff.txt', 'r').read()

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()

```

I thought it would output the results like this:
"http://www.stuff.co.nz/national/2344351/Vandals-ravage-motel-room" Vandals ravage motel room  (Palmerston North moteliers are fuming police did not act sooner after teenage boys trashed one of their rooms, causing $10,000 worth of damage.)

"http://www.stuff.co.nz/national/2344153/Motorcyclist-dies-after-skidding-off-road" Motorcyclist dies after skidding off road (A motorcyclist died last night after skidding off a road and into a stream. )

But I'm not getting the blank line between stories. Is the replace field in re.sub incorrect, or am I doing something else wrong?

Blair

---

