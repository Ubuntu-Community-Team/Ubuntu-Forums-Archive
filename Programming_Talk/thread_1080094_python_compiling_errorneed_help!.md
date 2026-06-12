---
title: "python compiling error:need help!"
date: 2009-02-25
forum: Programming Talk
---

### Post by AlexenderReez on 2009-02-25
i try to create a script that read specific webpage text and compare it to local text...
file.py
[PHP]import shutil
import os
import time
import datetime
import math
import urllib
from array import array

filehandle = urllib.urlopen('http://www.google.com')
myFile = open('TextOut.txt','w')

for lines in filehandle.readlines():
	print lines
	myFile.write(lines)

myFile.close()
filehandle.close() 

f1 = open('TextOut.txt').read().replace('\n',' ')
f2 = open('Dic.txt').read().replace('\n ',' ')
for w in f1.split(' '):
    if w in f2.split(' '):
       return "%s has match" % w

[/PHP]

Dic.py
> search

Groups

books

Books

text script contents error..i hope anybody can help me.tq

---

### Post by unutbu on 2009-02-25
If you change
```

      return "%s has match" % w  
```

to
```

        print "%s has match" % w  
```

then your script runs without error.
However, it also gives no output. The f1.split(' ') does not split up the TextOut.txt into recognizable words because the words you are looking for are not separated from the rest of the text by spaces. For example: this is in TextOut.txt:
```

class=gb2>Books</a>
```

If you are writing a little script and just need to get a little job done quickly, you might try splitting on '>' and '<', but I really dislike this strategy -- it feels ugly. 

If you plan on doing a lot of web scraping, time spent learning to use an HTML parser like BeautifulSoup ([http://www.crummy.com/software/BeautifulSoup/documentation.html](http://www.crummy.com/software/BeautifulSoup/documentation.html)) will payoff in the end.

What are you trying to do? Maybe we can suggest a better way.

---

### Post by AlexenderReez on 2009-02-25
> **unutbu said:**
> If you change
```

      return "%s has match" % w  
```

to
```

        print "%s has match" % w  
```

then your script runs without error.
However, it also gives no output. The f1.split(' ') does not split up the TextOut.txt into recognizable words because the words you are looking for are not separated from the rest of the text by spaces. For example: this is in TextOut.txt:
```

class=gb2>Books</a>
```

If you are writing a little script and just need to get a little job done quickly, you might try splitting on '>' and '<', but I really dislike this strategy -- it feels ugly. 

If you plan on doing a lot of web scraping, time spent learning to use an HTML parser like BeautifulSoup ([http://www.crummy.com/software/BeautifulSoup/documentation.html](http://www.crummy.com/software/BeautifulSoup/documentation.html)) will payoff in the end.

What are you trying to do? Maybe we can suggest a better way.

i want to create interactive application that ready website content and compare it with local words(in Dic.txt) so that i can determine type of website...whether it is good or bad website. any help is really appreciated . TQ :D

---

### Post by unutbu on 2009-02-25
Would this work for you? 
[PHP]#!/usr/bin/env python
import urllib
import re
import sys

if len(sys.argv)<2:
    print 'Usage: file.py URL'
    sys.exit(1)
else:
    url=sys.argv[1]
    if not url.startswith('http://'):
        url='http://'+url

# Download the webpage, save it in TextOut.txt
filehandle = urllib.urlopen(url)
myFile = open('TextOut.txt','w')
for lines in filehandle.readlines():
#     print lines
    myFile.write(lines)
myFile.close()
filehandle.close() 

f1 = open('TextOut.txt','r')
# contents contains the entire html webpage as one string
contents=f1.read()

f2 = open('Dic.txt')
# dic_words contains a list of words from Dic.txt. 
# You could in fact put regexp's in Dic.txt to do more
# sophisticated searches
dic_words=f2.read().split()


for dic in dic_words:
    # Search for the dic pattern in the contents string, ignoring case
    if re.search(dic,contents,re.IGNORECASE):
        print 'Match found: webpage contains the word %s'%dic[/PHP]

---

### Post by AlexenderReez on 2009-02-25
thanks a lot  :D  :KS :D

can you guide a bit more how to create simple interface that asking for link a website,which mean i don't need to modified the code every time i want to test other website

---

### Post by unutbu on 2009-02-25
I added some code so you can run the script like this:
```

file.py www.google.com
file.py ubuntuforums.org

```

Hope this helps.

---

### Post by AlexenderReez on 2009-02-25
> **unutbu said:**
> I added some code so you can run the script like this:
```

file.py www.google.com
file.py ubuntuforums.org

```

Hope this helps.

thanks a lot :D

---

