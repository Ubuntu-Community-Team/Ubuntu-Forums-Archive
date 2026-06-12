---
title: "Some code criticism?"
date: 2010-04-14
forum: Programming Talk
---

### Post by tom.swartz07 on 2010-04-14
Hi all,

Ive been working on a rather complex python script to try and grab my google reader feeds and display them in a concise output for the command line/conky.

I'm having some issues with the program failing mysteriously and I cannot, for the life of me, figure out why the code fails.

Could anyone take a peek at it and see what the problem is? Ill even add credit to you on the headers if you want! 

The code is hosted on my launchpad account- you could see it here:
[http://bazaar.launchpad.net/~tom-swartz07/%2Bjunk/main/annotate/head:/reader_parser.py](http://bazaar.launchpad.net/~tom-swartz07/%2Bjunk/main/annotate/head:/reader_parser.py)

Feel free to try any of my other files there, too. I wont mind! :D

Thanks!

---

### Post by tom.swartz07 on 2010-04-15
3 hour bump before bed?

---

### Post by tom.swartz07 on 2010-04-15
For those who dont feel like downloading the code and running it themselves, I have the error output here.

```
Traceback (most recent call last):
  File "./reader_parser.py", line 242, in <module>
    main()
  File "./reader_parser.py", line 239, in main
    greader.writeOutput()
  File "./reader_parser.py", line 106, in writeOutput
    unreadfeedcount, unreaditemtotalcount, feeds = self.getUnreadItems()
  File "./reader_parser.py", line 147, in getUnreadItems
    usock = urllib2.urlopen(url)
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 435, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 518, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 401: Unauthorized

```

---

### Post by tom.swartz07 on 2010-04-15
anyone?

---

### Post by lisati on 2010-04-15
Moved to "Programming Talk"

---

### Post by tom.swartz07 on 2010-04-16
Bumpity Bump?

I'm pretty much stuck at a standstill because of this error, I cant trace it back to any specific cause. 

As far as I know, all of the variables are correctly entered, the algorithms are syntactically correct, etc. 

I would greatly appreciate any help.

---

### Post by Zugzwang on 2010-04-16
Try opening a browser that you normally not use (e.g., konqueror) and enter the URL you are trying to fetch from. You are likely to get the same response. Develop a way to circumvent this problem, i.e., by figuring out how to log in beforehand.

---

### Post by tom.swartz07 on 2010-04-16
> **Zugzwang said:**
> Try opening a browser that you normally not use (e.g., konqueror) and enter the URL you are trying to fetch from. You are likely to get the same response. Develop a way to circumvent this problem, i.e., by figuring out how to log in beforehand.

The code creates a an authorized cookie for the application to use when logging in, isnt that the same way as logging in? 

I know Google has OAuth available for the accounts, but I have no idea whats involved with that, or how to implement it.

Ill try your method and report back. Thanks!

---

### Post by doas777 on 2010-04-16
well, since you're getting a 401, obviously it is not enough by itself to perform the login.

---

### Post by tom.swartz07 on 2010-04-16
> **doas777 said:**
> well, since you're getting a 401, obviously it is not enough by itself to perform the login.

Truth.

Ill see what I could do

---

### Post by doas777 on 2010-04-16
> **tom.swartz07 said:**
> Truth.

Ill see what I could do

you might be able to shell wget instead of using urllib
[http://www.linuxquestions.org/questions/linux-general-1/wget-to-login-to-a-website-659026/](http://www.linuxquestions.org/questions/linux-general-1/wget-to-login-to-a-website-659026/)

---

### Post by wmcbrine on 2010-04-16
urllib should be perfectly capable of handling this, but yes, you might need to do more than just accept cookies.

Here's some example code for a totally different "site" (the web server built into a TiVo), since I don't want to bother figuring out the Google site. Perhaps it will help:

```
auth_handler = urllib2.HTTPDigestAuthHandler()
cj = cookielib.LWPCookieJar()
tivo_opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj), 
                                   auth_handler)

### later in the code ###

auth_handler.add_password('TiVo DVR', tivoIP, 'tivo', tivo_mak)
return tivo_opener.open(url)
```

---

### Post by tom.swartz07 on 2010-04-16
Hokay.

I was digging around in some Google API's and I found a way to get the feed output in xml format, but now it doesnt seem to jibe with my current setup for parsing it and adding the unread counts....


Here is the code that I was able to use 'stand alone' to get the feed. Perhaps I might have to overhaul the entire program and re-do most of the classes.

```
#!/usr/bin/python
import urllib
import urllib2

username = 'xxx@gmail.com'
password = 'xxxxxxx'

# Authenticate to obtain SID
auth_url = 'https://www.google.com/accounts/ClientLogin'
auth_req_data = urllib.urlencode({'Email': username,
                                  'Passwd': password})
auth_req = urllib2.Request(auth_url, data=auth_req_data)
auth_resp = urllib2.urlopen(auth_req)
auth_resp_content = auth_resp.read()
auth_resp_dict = dict(x.split('=') for x in auth_resp_content.split('\n') if x)
SID = auth_resp_dict["SID"]

# Create a cookie in the header using the SID 
header = {}
header['Cookie'] = 'Name=SID;SID=%s;Domain=.google.com;Path=/;Expires=160000000000' % SID

reader_base_url = 'http://www.google.com/reader/api/0/unread-count?%s'
reader_req_data = urllib.urlencode({'all': 'true',
                                    'output': 'xml'})
reader_url = reader_base_url % (reader_req_data)
reader_req = urllib2.Request(reader_url, None, header)
reader_resp = urllib2.urlopen(reader_req)
reader_resp_content = reader_resp.read()

print reader_resp_content
```

Any ideas on how to chew through THIS output and get the unread count?

---

