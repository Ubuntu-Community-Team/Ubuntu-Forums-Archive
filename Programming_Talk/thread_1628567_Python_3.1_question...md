---
title: "Python 3.1 question.."
date: 2010-11-22
forum: Programming Talk
---

### Post by hopelessone on 2010-11-22
Hi,

I used to code in Basic in VB6 now i want to write my own Auto Electrical software and eventually invoicing system...I thought python would be the way to go..

I'm reading a book and i want to start making my software by extracting address and phone numbers, in a web page or text file i have:
```
<span id="listing-name-1">Bailey Crescent Auto Electrical</span> 
```
I want to extract the info ***Bailey Crescent Auto Electrical*** only...can you give me a sample to get going?

So far i got:
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

patterns=re.compile(r'(\name-1">\)|(\</span>\)') 

print(patterns)
```

doesn't work..yet

what do you think is the best way to go?

I really don't want to use BEAUTIFUL SOUP as i has probs in 3.1
and besides i want to search text files later using the modified code...

[http://www.python-forum.org/](http://www.python-forum.org/) wasn't beginner friendly...hoping you can get me started in python [or change languages?]

Many Thanks

---

### Post by Cheesehead on 2010-11-22
Regex usage (ignoring any issues with the regex itself):

patterns=re.compile(r'(\name-1">\)|(\</span>\)') 
result = patterns.search(text)
print(result)

---

### Post by mo.reina on 2010-11-23
regex isn't the best tool for the job.  i also wrote a quick parser for my own project using regex and it wasn't a good idea.

what you can use is the string.partition method

```

before, tag, text = string.partition(<beginning tag here>)
if tag:
  text, endtag, after = string.partition(<end tag here>)
  if endtag:
    print(text) #this is the text between the tags
  else:
    raise ValueError('Missing end tag ' + text) #no end tag to delimit the text

```
just place it in a loop, though you'll have to do it for every tag you have.  if you have different tag types it'll get quite cumbersome.

---

### Post by rkham11 on 2010-11-23
regex if used properly can be very effective

---

### Post by hopelessone on 2010-11-23
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

for line in text:
   before, tag, text = string.partition('<span id="listing-name-1">')
   if tag:
      text, endtag, after = string.partition('</span>')
      if endtag:
          print(text) #this is the text between the tags
      else:
          raise ValueError('Missing end tag ' + text) #no end tag to delimit the text


```

i get :
> Traceback (most recent call last):
  File "/mnt/hdd_1/Programming/Python/Addresses from Internet/qld.py", line 10, in <module>
    before, tag, text = string.partition('<span id="listing-name-1">')
AttributeError: 'list' object has no attribute 'partition'
>>> 

now in python did i finish the loop correctly? whats it complaining about?

Many Thanks

---

### Post by Arndt on 2010-11-23
> **hopelessone said:**
> ```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

for line in text:
   before, tag, text = string.partition('<span id="listing-name-1">')
   if tag:
      text, endtag, after = string.partition('</span>')
      if endtag:
          print(text) #this is the text between the tags
      else:
          raise ValueError('Missing end tag ' + text) #no end tag to delimit the text


```

i get :

> Traceback (most recent call last):
File "/mnt/hdd_1/Programming/Python/Addresses from Internet/qld.py", line 10, in <module>
before, tag, text = string.partition('<span id="listing-name-1">')
AttributeError: 'list' object has no attribute 'partition'
>>> 

now in python did i finish the loop correctly? whats it complaining about?

Many Thanks

It is complaining about the call string.partition, saying that 'string' does not have a 'partition' attribute, because it is actually a list. I don't see any assignment to 'string', so that must be done somewhere else in your program. Here is how 'partition' works:


```
>>> string = "bla bla <tag> blu blu"
>>> string.partition("<tag>")
('bla bla ', '<tag>', ' blu blu')
```

---

### Post by mo.reina on 2010-11-23
> **hopelessone said:**
> ```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

for line in text:
   before, tag, text = string.partition('<span id="listing-name-1">')
   if tag:
      text, endtag, after = string.partition('</span>')
      if endtag:
          print(text) #this is the text between the tags
      else:
          raise ValueError('Missing end tag ' + text) #no end tag to delimit the text


```

i get :


now in python did i finish the loop correctly? whats it complaining about?

Many Thanks

you have to replace *string* with whatever variable you're using for your text.  in your case, since you've assigned the html page to **text**, it should be:
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

before, tag, txt = text.partition('<span id="listing-name-1">') # before = text before the tag, tag = <span id>, txt = text after the tag

while txt:
   
   txt, endtag, after = txt.partition('</span>') txt = text before the end tag, endtag = </span>, after = text after the endtag

      if endtag:
          print(txt) #this is the text between the tags
      else:
          raise ValueError('Missing end tag ' + txt) #no end tag to delimit the text

   before, tag, txt = after.partition('<span id="listing-name-1">') #repeat 
```

---

### Post by hopelessone on 2010-11-23
Thanks for explaining mo.reina ! you made my day !

---

