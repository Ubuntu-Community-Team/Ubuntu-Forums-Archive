---
title: "Python Picture of the Day"
date: 2009-06-18
forum: Programming Talk
---

### Post by curvedinfinity on 2009-06-18
Here's a short script that grabs the Wikipedia Picture of the Day:

```

#!/usr/bin/python

import urllib2

potdMeta = urllib2.urlopen('http://toolserver.org/~daniel/potd/commons/potd.meta.xml')
potdURL = potdMeta.read().split('url="')[1].split('"')[0]
potdRequest = urllib2.Request(potdURL)
potdRequest.add_header('User-Agent','OpenAnything/1.0')
potd = urllib2.build_opener().open(potdRequest)
f = open('./potd.jpg','wb')
f.write(potd.read())
f.close()

```

Just a fun script. :)

---

### Post by smartbei on 2009-06-19
You may want to change the 'w' in the open function call to 'wb', to prevent the os from potentially changing percieved line endings in the jpeg file.
Nice though!

EDIT: I implemented this with an xml parser also, just to see how much work it would be - turns out it isn't worth it.

---

### Post by curvedinfinity on 2009-06-19
I made it so I can make my own homepage like Google/ig or bing. Here's a script for getting the top headlines from wikinews:

```

#!/usr/bin/python

import urllib2

wikinews = urllib2.urlopen('http://feeds.feedburner.com/WikinewsLatestNews')
newsItems = wikinews.read().split('<item>')[1:5]
for newsItem in newsItems:
	title = newsItem.split('<title>')[1].split('</title>')[0]
	print title
	link = newsItem.split('<link>')[1].split('</link>')[0]
	print link

```

It just prints them, but it would be easy to do something else with them. :)

---

