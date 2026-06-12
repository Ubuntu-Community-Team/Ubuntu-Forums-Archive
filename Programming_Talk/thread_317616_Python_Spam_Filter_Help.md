---
title: "Python Spam Filter Help"
date: 2006-12-12
forum: Programming Talk
---

### Post by vbnet2005 on 2006-12-12
hi there. i have an small exercise to write a basic spam filter but im stuck on some stuff


```

#!/usr/bin/python

import getpass, imaplib, string
from StringIO import StringIO

#
#  getBody - strips of the header from an email message
#            Only the body of the message is returned.
#

def getBody(message):
    body=""
    seenStart = 0
    for line in StringIO(message).readlines():
        l = string.strip(line)
        if (seenStart == 1):
            body = body + "\n" + l
        elif l == "":
            seenStart = 1
    return body

#
#  getField - returns the field value "field" in the header
#             section of the message
#

def getField(message, field):
    for line in StringIO(message).readlines():
        l = string.strip(line)
        if (string.find(l, field) != -1):
            words = string.split(l, field)
            return words[1]
    return "unknown"


#
#  containsTag - returns TRUE if an html tag <'t' is found
#
            
def containsTag(l, t):
    return ((string.find(l, "<" + t) != -1) or
            (string.find(l, "</" + t) != -1))

#
#  isSpam - returns 1 if the message looks like spam
#           returns 0 if the message looks ok
#

def isSpam(message):
    total = 0
    htmlFound = 0
    for line in StringIO(getBody(message)).readlines():
        print line
   [b] # incomplete and at the moment everything is treated as
    # non spam[/b]
    return 0
        

#
# postEmail - sends message to the smtp port
#

def postEmail(message):
    print "message from", getField(message, "From:")
    print "subject is", getField(message, "Subject:")
    **# incomplete**

#
#  handleEmail - tests whether the message is spam or not.
#                If spam then it adds it to a file
#                otherwise post it to the smtp port
#

def handleEmail(message):
    if (isSpam(message)):
        print "message is spam"
    else:
        print "message is good"
        postEmail(message)
    **# incomplete**
    

#
#  collectEmail - retrieves the email from the imap server
#

def collectEmail():
    m = imaplib.IMAP4_SSL('url here')
    m.login(getpass.getuser(), getpass.getpass())
    m.select()
    typ, data = m.search(None, 'ALL')
    print data
    for num in string.split(data[0]):
        print num
        typ, data = m.fetch(num, '(RFC822)')
        handleEmail(data[0][1])
    m.logout()

collectEmail()

the methods i have to complete are listed below.

def isSpam(message):
def postEmail(message):
def handleEmail(message):

basically i have to check each line of the email and if html > 60% of the email then it is considerd as SPAM .
```

ive started some of the missing codes but i dont know how to finish them off. any help is apprechiated. thanks alot

---

### Post by dwblas on 2006-12-13
I know of this spam filter written in Python.  Perhaps looking at the source will help.  [http://spambayes.sourceforge.net](http://spambayes.sourceforge.net)

---

