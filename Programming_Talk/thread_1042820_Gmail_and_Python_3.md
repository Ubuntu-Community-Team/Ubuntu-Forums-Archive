---
title: "Gmail and Python 3"
date: 2009-01-17
forum: Programming Talk
---

### Post by TheAxeR on 2009-01-17
I have a script which I use with conky to tell me the unread count and the title of unread emails.  I did not write the original script; but, I made a few changes and everything worked fine.  I then decided I would give a try at changing it to work with python 3.  I have run into an error which I do not understand.  

Here is the code:
```

import sys
import urllib.request
from xml.dom.minidom import parse


gmail = 'https://mail.google.com/gmail/feed/atom'

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]


def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    
    # Create an OpenerDirector with support for Basic HTTP Authentication...
    auth_handler = urllib.request.HTTPBasicAuthHandler()
    auth_handler.add_password(realm='New mail feed',
                              uri='https://mail.google.com/',
                              user= uname,
                              passwd= password)
    opener = urllib.request.build_opener(auth_handler)
    # ...and install it globally so it can be used with urlopen.
    urllib.request.install_opener(opener)
    response = urllib.request.urlopen(gmail)
    feed = response.read()  
    return feed

def read_mail(feed, maxlen):
    '''Parse the Atom feed and print a summary'''

    atom = parse(feed)
    
    num_email = atom.getElementsByTagName(fullcount)
    
    # Output the total number of new emails.
        
    if num_email > 1:
        print ('${color1} {0} new emails\n').format(num_email)
    elif num_email == 1:
        print ('${color1} {0} new emails\n').format(num_email)
    else:
        print ('${color1} No new emails\n')
        
if __name__ == "__main__":
    
    mailfeed = get_feed()            # Do auth and then get the feed
    read_mail(mailfeed, int(maxlen)) # Let the feed be chewed by feedparser

```

Here is the error:
> 
Traceback (most recent call last):
  File "conkyGmail2.py", line 96, in <module>
    read_mail(mailfeed, int(maxlen)) # Let the feed be chewed by feedparser
  File "conkyGmail2.py", line 64, in read_mail
    atom = parse(feed)
  File "/usr/lib/python3.0/xml/dom/minidom.py", line 1917, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 928, in parse
    result = builder.parseFile(file)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 204, in parseFile
    buffer = file.read(16*1024)
AttributeError: 'bytes' object has no attribute 'read'


It seems that there is an issue when it tries to read the atom file which Google supplies.


I have based this on this code for python 2.5, which I know works:

```


import sys
import urllib             # For BasicHTTPAuthentication
import feedparser         # For parsing the feed



GMAIL = "https://mail.google.com/gmail/feed/atom"

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]


urllib.FancyURLopener.prompt_user_passwd = lambda self, host, realm: (uname, password)

def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    opener = urllib.FancyURLopener()
    f = opener.open(GMAIL)
    feed = f.read()
    return feed

def read_mail(feed, maxlen):
    '''Parse the Atom feed and print a summary'''
    
    atom = feedparser.parse(feed)
    
    num_email = len(atom.entries)
    

    # Output the total number of new emails.
        
    if num_email > 1:
        print '${color1} %s new emails\n' % (len(atom.entries))
    elif num_email == 1:
        print '${color1} %s new emails\n' % (len(atom.entries))
    else:
        print '${color1} No new emails\n'
        
    for i in range(min(len(atom.entries), maxlen)):
       
        mail = atom.entries[i]
        title_len = len(mail.title)
        
        # Test that the email has a subject line.  If it does not have a subject 
        # line then use the author.
        
        if title_len == 0:
            title = mail.author
        else:
            title = mail.title
            

        # Truncate if the email subject line is longer then 20 characters.
        # This includes spaces.  If it is longer add ellipse.

        if len(title) < 21:
            print '          ${color2}%s' % title
        else:
            print '          ${color2}%s...' % title[:20]
            
#uncomment the following line if you want to show the name of the sender
#       print '          ${color2}%s' % atom.entries[i].author

    if len(atom.entries) > maxlen:
        print ' ${color}more...'

if __name__ == "__main__":
    
    f = get_feed()            # Do auth and then get the feed
    read_mail(f, int(maxlen)) # Let the feed be chewed by feedparser

```

Any help would be appreciated.  Thank you.

---

### Post by croto on 2009-01-18
Hi,

I don't have Python 3.0 installed to try out your code, but I think there are two bugs. 

The method "parse" from xml.dom.minidom doesn't take a string as an input but a file to parse. The method you want is "parseString". I think you should change the line "atom=parse(feed)" to "atom=parseString(feed)". Also, you should import that method. Change the import line to "from xml.dom.minidom import parseString".

The second problem I see is 

num_email = atom.getElementsByTagName(fullcount)

Did you mean
num_email = atom.getElementsByTagName("fullcount")
?

---

### Post by TheAxeR on 2009-01-18
Thank you for the response.  

I tried using parseString, however, it now gives this error:

```
Traceback (most recent call last):
  File "conkyGmail2.py", line 95, in <module>
    read_mail(mailfeed, int(maxlen)) # Let the feed be chewed by feedparser
  File "conkyGmail2.py", line 63, in read_mail
    atom = parseString(feed)
  File "/usr/lib/python3.0/xml/dom/minidom.py", line 1927, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 940, in parseString
    return builder.parseString(string)
  File "/usr/lib/python3.0/xml/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: syntax error: line 1, column 0

```

My initial guess is that the feed is not properly formatted, or, python expects a different format.



I did not make any big changes but here is the most recent version I have tested.
```
import sys
import urllib.request
from xml.dom.minidom import parse, parseString

gmail = 'https://mail.google.com/gmail/feed/atom'

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]


def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    
    # Create an OpenerDirector with support for Basic HTTP Authentication...
    auth_handler = urllib.request.HTTPBasicAuthHandler()
    auth_handler.add_password(realm='New mail feed',
                              uri='https://mail.google.com/',
                              user= uname,
                              passwd= password)
    opener = urllib.request.build_opener(auth_handler)
    # ...and install it globally so it can be used with urlopen.
    urllib.request.install_opener(opener)
    response = urllib.request.urlopen(gmail)
    feed = response.read() 
    return feed
    


def read_mail(feed, maxlen):
    '''Parse the Atom feed and print a summary'''

    atom = parseString(feed)
    
    num_email = atom.getElementsByTagName("fullcount")
    
    # Output the total number of new emails.
        
    if num_email > 1:
        print ('${color1} {0} new emails\n').format(num_email)
    elif num_email == 1:
        print ('${color1} {0} new emails\n').format(num_email)
    else:
        print ('${color1} No new emails\n')
if __name__ == "__main__":
    
    mailfeed = get_feed()            # Do auth and then get the feed
    read_mail(mailfeed, int(maxlen)) # Let the feed be chewed by feedparser

```

---

### Post by croto on 2009-01-18
Hey man,

sorry I gotta run now. I translated your code back to python 2.6, and made it a bit simpler to make sure things work the way they're supposed to:
```

import sys
import urllib2
from xml.dom.minidom import parse, parseString

gmail = 'https://mail.google.com/gmail/feed/atom'

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]


def get_feed():
    '''The method to do HTTPBasicAuthentication'''
    
    # Create an OpenerDirector with support for Basic HTTP Authentication...
    auth_handler = urllib2.HTTPBasicAuthHandler()
    auth_handler.add_password(realm='New mail feed',
                              uri='https://mail.google.com/',
                              user= uname,
                              passwd= password)
    opener = urllib2.build_opener(auth_handler)
    # ...and install it globally so it can be used with urlopen.
    urllib2.install_opener(opener)
    response = urllib2.urlopen(gmail)
    feed = response.read() 
    return feed
    


def read_mail(feed, maxlen):
    '''Parse the Atom feed and print a summary'''

    print feed
    atom = parseString(feed)
    print atom
        
if __name__ == "__main__":
    
    mailfeed = get_feed()            # Do auth and then get the feed
    read_mail(mailfeed, int(maxlen)) # Let the feed be chewed by feedparser


```

When I run it from the command line:
```

python test.py <user> <pass> 100000

```
it works fine, meaning: the feed is read correctly (output of "print feed"); and the xml is parsed without errors. 

I would suggest you print the feed without parsing it, to make sure that part is working fine on your end.

Then, from the Python 3 library documentation [http://docs.python.org/3.0/library/xml.dom.minidom.html]("http://docs.python.org/3.0/library/xml.dom.minidom.html"), I got this little example:
```

import xml.dom.minidom

document = """\
<slideshow>
<title>Demo slideshow</title>
<slide><title>Slide title</title>
<point>This is a demo</point>
<point>Of a program for processing slides</point>
</slide>

<slide><title>Another demo slide</title>
<point>It is important</point>
<point>To have more than</point>
<point>one slide</point>
</slide>
</slideshow>
"""

dom = xml.dom.minidom.parseString(document)

print dom

```
which is just parsing an xml string. Make sure this works too.

I'll be out most of today, but I'll check back later.

---

### Post by TheAxeR on 2009-01-18
So I tested it against the document you pointed at.  I also downloaded the atom feed as a file and tried parsing that.  In both instances everything worked.  

I then decided to try another feed.  The one I tested is

[http://www.feedparser.org/tests/wellformed/atom/entry_author_email.xml]("http://www.feedparser.org/tests/wellformed/atom/entry_author_email.xml")

This also worked.  Here is the dom followed by the file itself printed to the terminal:

> 
<xml.dom.minidom.Document object at 0xb7909aac>

b'<!--\r\nDescription: entry author email\r\nExpect:      not bozo and entries[0][\'author_detail\'][\'email\'] == u\'me@example.com\'\r\n-->\r\n<feed version="0.3" xmlns="http://purl.org/atom/ns#">\r\n<entry>\r\n  <author>\r\n    <name>Example author</name>\r\n    <email>me@example.com</email>\r\n    <url>http://example.com/</url>\r\n  </author>\r\n</entry>\r\n</feed>'


When I try the gmail feed, the file printed to the terminal is:
> 
b'162\r\n<?xml version="1.0" encoding="UTF-8"?>\n<feed version="0.3" xmlns="http://purl.org/atom/ns#">\n<title>Gmail - Inbox for [email]EMAIL@gmail.com[/email]</title>\n<tagline>New messages in your Gmail Inbox</tagline>\n<fullcount>0</fullcount>\n<link rel="alternate" href="http://mail.google.com/mail" type="text/html" />\n<modified>2009-01-18T18:12:45Z</modified>\n</feed>\n\r\n0\r\n\r\n'


The error 
> xml.parsers.expat.ExpatError: syntax error: line 1, column 0
seems to be saying that python has an issue with the 
> 162\r\n
at the beginning of the feed.  It seems weird that if I download the feed as a file the 162 part is not there.


So it seems that by striping the offending characters from the beginning and end of the string everything works fine.  

Thank you for your help.  I will keep this in mind next time I have to parse some xml.

---

### Post by croto on 2009-01-18
Ok, so things seem to be clearer now... however, that 162 is strange, moreover taking into account that you don't get that when you download the feed as a file. Anyways, what matters is that it's working fine now. 

Good luck!

---

