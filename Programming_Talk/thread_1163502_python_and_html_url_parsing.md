---
title: "python and html url parsing"
date: 2009-05-18
forum: Programming Talk
---

### Post by meg23 on 2009-05-18
I am trying to write a script that grabs urls from news websites and parses the links into html. Here is the script:
```

#! /usr/bin/python
a = '<a href="'
b = open('/home/moshe/Desktop/headlines.txt','r')
data = b.readlines()
c = '">click here</a>'
x = [1,2,3,4,5]
for v in x:
	print data[v]
import os
print os.system("elinks -dump http://www.investors.com | grep -v Default | grep http | grep Newsfeed | awk '{print $2}' > /home/moshe/Desktop/headlines.txt")
print '<p>'
print str(a) + str(data[v]) + str(c)
print '</p>'
print " "
```

Unfortunately, it only parses the last url in the way I want it to. Here is the result:

```
http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94386435&source=Newsfeed

http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94384101&source=Newsfeed

http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94386541&source=Newsfeed

http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94386435&source=Newsfeed

http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94384101&source=Newsfeed

0
<p>
<a href="http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94384101&source=Newsfeed
">click here</a>
</p>
```
 
Anyone have an idea how to fix this?

---

### Post by ghostdog74 on 2009-05-18
use Python's urllib or urllib2 module to get web pages...then use a HTML parser such as Beautifulsoup to get those links
you do not need to call shell commands in Python, at least for what you are doing... It makes your code ugly and "non portable". Simple example without hTML parser.
```

import urllib2
url="http://www.investors.com"
page=urllib2.urlopen(url)
result = page.read()
result = result.split("href=\"")
for i in  result:
    if "http://" in i and "Newsfeed" in i:
        s=i.index("\">")
        print i[:s]


```
output:
```

# ./test.py
http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94386541&amp;source=Newsfeed
http://www.investors.com/NewsAndAnalysis/Article.aspx?id=94386435&amp;source=Newsfeed


```

---

### Post by UbuKunubi on 2009-05-19
My weapon of choice when it comes to python and screen scraping is Beautifulsoup.

[http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

Hope this is of some use.

---

### Post by simeon87 on 2009-05-19
It only parses the last URL because you haven't placed the code in the for loop. The variable v now has the value 5 which is the last one. If you want to parse them all, you have to put everything in the for loop:

```

for v in x:
    print os.system("elinks -dump http://www.investors.com | grep -v Default | grep http | grep Newsfeed | awk '{print $2}' > /home/moshe/Desktop/headlines.txt")
    print '<p>'
    print str(a) + str(data[v]) + str(c)
    print '</p>'
    print " "

```

Also see at the previous topic: [http://ubuntuforums.org/showthread.php?t=1163360](http://ubuntuforums.org/showthread.php?t=1163360).

---

