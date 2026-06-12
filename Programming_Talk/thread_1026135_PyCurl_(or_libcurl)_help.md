---
title: "PyCurl (or libcurl) help"
date: 2008-12-30
forum: Programming Talk
---

### Post by pokerbirch on 2008-12-30
I'm learning Python. Most of my programs download data from various websites, so i'm building a simple, re-usable class that i can use to retrieve the html of a given url. There are times when i need high performance, so for that reason i've chosen PyCurl.

Documentation for PyCurl is poor and i've been reading the curl/libcurl sites to try and work out how do use the damn library. It seems fairly straight forward once you work out how to set the options:
```

import pycurl

USER_AGENT = 'Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5'

c = pycurl.Curl()
c.setopt(pycurl.VERBOSE, 1) # show request info
c.setopt(pycurl.COOKIEFILE, '') # enable automatic cookie handling
c.setopt(pycurl.ENCODING, 'gzip, deflate')
c.setopt(pycurl.USERAGENT, USER_AGENT)
c.setopt(pycurl.CONNECTTIMEOUT, 5)
c.setopt(pycurl.TIMEOUT, 5)
c.setopt(pycurl.URL , 'http://whatsmyuseragent.com')
c.perform()
c.close

```
Now there may be mistakes in the above...which is why i'm asking for a little help. First of all, is the COOKIEFILE parameter correct? From the libcurl docs, it says that the cookie parser can be enabled by specifying a none-existent file...does an empty string qualify as a none existent file? Secondly, the page source is printed out to the console (which shows me that it's working ok), but i actually don't want it to do that. I want the data to be returned as a string so that i can then forward into a parsing routine. As much as i've Googled, i just can't seem to find out how to get the response as a string.

It's probably a one-liner solution, just to make me feel more stupid. :P

---

### Post by pokerbirch on 2008-12-31
Have done some more reading, am i correct in thinking that in order to return a string, i need to use callbacks via pycurl.WRITEFUNCTION and (if required) pycurl.HEADERFUNCTION? I guess that would require appending to a global string or something like that?

I can't believe how poor the documentation is, considering it is such a well known library. :confused:

---

### Post by mike_g on 2008-12-31
> Have done some more reading, am i correct in thinking that in order to return a string, i need to use callbacks via pycurl.WRITEFUNCTION and (if required) pycurl.HEADERFUNCTION?
Return a string from what? 

From what I can tell WRITEFUNCTION points to to a callback function that you should use to save the content. You wont need to use a global string for it. The basic pycurl example in the docs shows it stored in a class:
```
#! /usr/bin/env python
# -*- coding: iso-8859-1 -*-
# vi:ts=4:et
# $Id: basicfirst.py,v 1.5 2005/02/11 11:09:11 mfx Exp $

import sys
import pycurl

class Test:
    def __init__(self):
        self.contents = ''

    def body_callback(self, buf):
        self.contents = self.contents + buf

print >>sys.stderr, 'Testing', pycurl.version

t = Test()
c = pycurl.Curl()
c.setopt(c.URL, 'http://www.google.co.uk')
c.setopt(c.WRITEFUNCTION, t.body_callback)
c.perform()
c.close()

print t.contents
```

And yeah, I agree that python wrappers often have poor docs. Sometimes I find it helps to read the docs for the original libraries and guess the rest.

---

### Post by pokerbirch on 2008-12-31
Ok then how's about this?
```

import pycurl
from cStringIO import StringIO

USER_AGENT = 'Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5'

class scraper(object):
    def __init__(self):
        self.stringbuf = StringIO()
        self.c = pycurl.Curl()
        self.c.setopt(pycurl.VERBOSE, 1) # show request info
        self.c.setopt(pycurl.COOKIEFILE, '') # enable automatic cookie handling
        self.c.setopt(pycurl.ENCODING, 'gzip,deflate')
        self.c.setopt(pycurl.USERAGENT, USER_AGENT)
        self.c.setopt(pycurl.CONNECTTIMEOUT, 5)
        self.c.setopt(pycurl.TIMEOUT, 5)

    def __curl_callback(self, buf):
        self.stringbuf.write(buf)

    def gethtml(self, url):
        self.c.setopt(pycurl.URL , url)
        self.c.setopt(pycurl.WRITEFUNCTION, self.__curl_callback)
        self.c.setopt(pycurl.HEADERFUNCTION, self.__curl_callback)
        self.c.perform()
        self.c.close
        return self.stringbuf.getvalue()

s = scraper()
print s.gethtml('http://whatsmyuseragent.com')

```

Seems to be doing what i expect now. Not forgetting that i'm still relatively new to Python, is the general style/usage of my code ok? I'm pretty sure i've got the whole OOP thing sussed out but there could be mistakes...

Now, you may have noticed that i'm a bit of a performance freak, hence why:
* i'm using libcurl
* i'll be adding libxml for some SOAP stuff i have planned
* i used cStringIO instead of StringIO
* i chose to concatenate the callback to a string buffer rather than just use self.string += buf

I suppose that all i want really, is confirmation from some python 'experts' that i'm actually using Python correctly?

---

### Post by pokerbirch on 2008-12-31
> **mike_g said:**
> From what I can tell WRITEFUNCTION points to to a callback function that you should use to save the content.
Great minds think alike, i was writing my reply, then went for tea, then finished it off....meanwhile you'd posted and i hadn't read it. :)

> **mike_g said:**
> And yeah, I agree that python wrappers often have poor docs. Sometimes I find it helps to read the docs for the original libraries and guess the rest.
PyCurl is actually quite a simple library IF you know how to use it. I've read pages and pages of libcurl docs in order to work out what to do. I also found the PHP docs were quite useful as curl is a part of the PHP standard library.

All i have to do now is write a similar class for libxml. :rolleyes:

---

