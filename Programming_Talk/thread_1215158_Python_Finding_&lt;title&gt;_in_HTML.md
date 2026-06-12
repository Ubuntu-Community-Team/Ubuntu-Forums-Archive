---
title: "Python: Finding &lt;title&gt; in HTML"
date: 2009-07-16
forum: Programming Talk
---

### Post by gazmac on 2009-07-16
Hi,

I have been struggling with this all day and would appreciate a little nudge in the right direction.

I have an html file saved on my harddrive in the same location as my python script. Lets call it page.html

The page.html has a very standard format for example...

```
header stuffheader stuffheader stuffheader stuff
header stuffheader stuffheader
stuffheader stuffheader stuff...
<title>
Very Interesting Title That I need to know
</title>
bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff 
bodystuff bodystuff bodystuff bodystuff
bodystuff bodystuff INTERESTING: number bodystuff 
bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff bodystuff 
bodystuff....
```

I am trying to write a python script that stores the string between the <title> tags as a variable for printing or storing in a database. That's priority number one.

A nice to have would be if it also found the word "INTERESTING:" in the body text and stored everything after it until the next 'bodystuff'.

I have already tried to use Beautiful Soup on this with no success as it fails to parse this particular HTML for some reason.

I believe that regular expressions might be the way forward, but the Title is always spread out over three lines and I am struggling to get results.
```
<title>
Very Interesting Title That I need to know
</title>

```

So far I have used this to get the page.html into python...
```

list = file("page.html","r")
for line in list:

```

which seems to work, but how to get the interesting 0.5% back out? 

Thanks, gazmac

---

### Post by unutbu on 2009-07-16
Here is a script that uses the string method find() to locate the first occurrence of <title> and </title> and return everything in between.

Note that the script uses fh.read() -- the entire page.html is read into a variable as one giant string. If page.html is very long, then the script can be modified to be less memory-intensive, at the price of being a little more complicated. If page.html is short this script should do.

[PHP]#!/usr/bin/env python
def everything_between(text,begin,end):
    idx1=content.find(begin)
    idx2=content.find(end,idx1)
    return content[idx1+len(begin):idx2].strip()

content=open('page.html').read()
title=everything_between(content,'<title>','</title>')
interesting=everything_between(content,'INTERESTING:','bodystuff')
print(title)
print(interesting)
[/PHP] returns```

Very Interesting Title That I need to know
number
```

---

### Post by Dill on 2009-07-16
Try using BeautifulSoup, an HTML parser. You can install it via apt-get:

```
sudo apt-get install python-beautifulsoup
```

Then, just parse away!

```
#!/usr/bin/python

import urllib2
from BeautifulSoup import BeatifulSoup

# Open URL, read HTML, and find title
URLObject = urllib2.urlopen('http://yourwebpage.com')
html = BeautifulSoup(URLObject.read())
data = html.find('title')

# Print title
print data.contents[0]

```

Cheers,
Dill

---

### Post by ghostdog74 on 2009-07-16
> **unutbu said:**
> 

```

...
fh=open('page.html')
content=''.join(fh.readlines())
```

why not just 
```

content=open("page.html).read()

```

@OP, just another way
```

import re
pat = re.compile("<title>(.*?)<\/title>",re.DOTALL|re.M)
pat1 = re.compile(".*(INTERESTING.*?)bodystuff",re.DOTALL|re.M)
data=open('file').read()
print pat.findall(data)[0]
print pat1.findall(data)[0]

```

---

### Post by unutbu on 2009-07-16
> **ghostdog74 said:**
> why not just 
```

content=open("page.html).read()

```

Indeed. Thanks :)

---

### Post by master_kernel on 2009-07-17
Personally, I prefer regex, as mentioned above by ghostdog. But it's really personal preference.

---

### Post by Jacks0n on 2009-07-18
```

a = open('index.html', 'r')
print a.read().split('<title>')[1].split('</title>')[0].strip()

```

---

