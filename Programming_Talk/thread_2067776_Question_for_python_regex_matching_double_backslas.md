---
title: "Question for python regex: matching double backslashes '\\'"
date: 2012-10-07
forum: Programming Talk
---

### Post by kpuz on 2012-10-07
Hi,
I am writing a script to scrape urls from a website. The following is the string I'm trying to match (it is found in the page source read by urllib2.urlopen(webpage).read()):
```

"stream_h264_url":"http:\\/\\/www.dailymotion.com\\/cdn\\/H264-512x384\\/video\\/xu41s3.mp4?auth=1349806412-337e4c35a8590a1dabc2761376070386"
```

The regex search I do in python is:
```
re.search('"stream_h264_url":"http:[-\\/a-zA-Z0-9?=.]+"',html)
```

where html is the page source of the webpage I'm interested in.

But I get an error saying: unexpected end of regular expression.
If I change the regex from,

**'"stream_h264_url":"http:[-\\/a-zA-Z0-9?=.]+"'**

to

**'"stream_h264_url":"http:[-\\\\/a-zA-Z0-9?=.]+"'**

everything matches perfectly. But I don't understand why I have to match two backslashes as opposed to a single literal backslash. Shouldn't a literal backslash ('\\') match every single backslash in the page source?

Any help is appreciated.

---

### Post by epicoder on 2012-10-07
Python also uses the backslash as a special escaping character. Two backslashes will expand to one. It will expand "\\" to "\" and "\\\\" to "\\".  To avoid needing rediculous amounts of backslashes, you can use a raw string:
```
r'"stream_h264_url":"http:[-\\/a-zA-Z0-9?=.]+"'
```
The 'r' before the string causes python to interpret the string literally, ignoring escape sequences.

---

### Post by greenpeace on 2012-10-08
I would (almost always) recommend beautifulsoup for parsing HTML:  [http://www.crummy.com/software/BeautifulSoup/bs4/doc/](http://www.crummy.com/software/BeautifulSoup/bs4/doc/)

Something like the following would be appropriate for extracting all href attributes from the <a> tags on the page:

```
#!/usr/bin/python
import urllib2
from bs4 import BeautifulSoup

url  = 'http://ubuntu.com'
html = urllib2.urlopen(url).read()
soup = BeautifulSoup(html)

# find all <a> tags
for a in soup.find_all('a'):

  # extract the href attribute
  link = a.get('href')

  # only print full URLs
  if link[:7] == "http://":
    print link

```


Hope it helps!

g

---

