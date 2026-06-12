---
title: "Convert Unicode Literals to Symbols"
date: 2007-05-12
forum: Programming Talk
---

### Post by smartbei on 2007-05-12
I have a website I am working on that is in both English and Hebrew. For Hebrew right now they are using &#<####>; notation, so for example &#1488; = the first letter of the hebrew alphabet. What I am trying to do is change the encoding on all the pages to utf-8 and convert using a python script all the &#<####>; into the actual  unicode symbol represented by the notation. For some reason, I am not succeeding:

```

ret=r'&#(\d{4});' #The regular expression, using a group to capture the  4-digit number
import re
cre=re.compile(ret)
a='&#1512;&#1490;&#1500;&#1505;&#1493;&#1503;' #Just a test case

def toUni(match):
	#This is the part that does not work. I have tried several different options below, and am not able to get it to convert he character to hebrew.

s=cre.sub(toUni,a)


```

What I am looking for is what I need to put in toUni() so that the output is a unicode symbol. I have also tried using a.encode('utf-8') or something of the sort, but that doesn't seem to work either.

---

### Post by cwaldbieser on 2007-05-12
> **smartbei said:**
> I have a website I am working on that is in both English and Hebrew. For Hebrew right now they are using &#<####>; notation, so for example &#1488; = the first letter of the hebrew alphabet. What I am trying to do is change the encoding on all the pages to utf-8 and convert using a python script all the &#<####>; into the actual  unicode symbol represented by the notation. For some reason, I am not succeeding:

```

ret=r'&#(\d{4});' #The regular expression, using a group to capture the  4-digit number
import re
cre=re.compile(ret)
a='&#1512;&#1490;&#1500;&#1505;&#1493;&#1503;' #Just a test case

def toUni(match):
	#This is the part that does not work. I have tried several different options below, and am not able to get it to convert he character to hebrew.

s=cre.sub(toUni,a)


```

What I am looking for is what I need to put in toUni() so that the output is a unicode symbol. I have also tried using a.encode('utf-8') or something of the sort, but that doesn't seem to work either.
Maybe this link will help:
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/303668]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/303668")

---

