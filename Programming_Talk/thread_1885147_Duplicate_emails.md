---
title: "Duplicate emails"
date: 2011-11-22
forum: Programming Talk
---

### Post by CoffeeRain on 2011-11-22
Hi! I'm trying to make a web scraper in python. This is just for me to learn, and not for anything illegal or spamming. Anyways, my computer isn't fast enough to do that. I have tried to keep it from writing duplicate email addresses in a file. When I make a list of all the email addresses and print it, the list gets printed as a list. When I say ```
if my_list.__contains__(item):
pass
``` I still get duplicate emails. Is it because of the use of pass? I have been able to shorten it other ways, like my_list = list(set(my_list)) of all the emails on a page, but that just thins the number, and doesn't keep duplicates out.

---

### Post by CoffeeRain on 2011-11-28
Wow. So many views and no replies. :(

---

### Post by 11jmb on 2011-11-28
Perhaps posting a bit more code? It is hard to tell what you are doing without more context.

I have only ever used pass as a place-holder for a function that does nothing. Are you trying to exit the function with pass? that is a job for return.

---

### Post by CoffeeRain on 2011-11-28
You could ask me for what snippet of code you want, but about pass... I assumed it just did nothing. Would there be a more appropriate command to exit the if statement? I'll check the docs on return.

---

### Post by HotCupOfJava on 2011-11-28
I'm not as familiar w/ Python as Java, but if you are checking to see if your list contains something, you might want to make sure that the interpreter isn't seeing your "duplicate" emails as different items. They may look the same, but still be treated as different objects by the interpreter, because they refer to different Python objects. You may have to find a different means of comparing the emails.

---

### Post by cgroza on 2011-11-28
And why do you use __contains__?
That is not pythonic at all.
What's wrong with "in" ?
```

if item in emails:
     pass

```

---

### Post by Bodsda on 2011-11-29
> ```
if my_list.__contains__(item):
pass
```Ignoring the fact that that code won't work due to indentation problems, why check for a condition, then ignore it if its true? Presumably you then have an else block that runs, thats just a waste of lines 

```

if item in my_list:
    pass
else:
    append item to my list

```try this instead

```

if item not in my_list:
    append item to my list

```> 
 When I make a list of all the email addresses and print it, the list gets printed as a list.
What were you expecting to happen when you print a list? I'd be disappointed if printing a list didn't print a list

If you want to print each individual entry in a list, use a loop.
```

for address in my_list:
    print address

```When asking for help it is important to show us all the code. We can't help you to understand why your program is not behaving the way you expect it to if we can't see exactly what it is doing.

Bodsda

---

### Post by 11jmb on 2011-11-29
> **CoffeeRain said:**
> You could ask me for what snippet of code you want, but about pass... I assumed it just did nothing. Would there be a more appropriate command to exit the if statement? I'll check the docs on return.

It seems to me like you want to use the set data structure for this problem. A set will use a hash function for any immutable object (including string literals and primitives) to prevent any duplicates from being stored.

[http://greeennotebook.com/2010/06/python-sets-tutorial/](http://greeennotebook.com/2010/06/python-sets-tutorial/)

Why re-invent the wheel?

---

### Post by CoffeeRain on 2011-11-29
Thanks! It's working much better now. Another question... Is there a way to make the scraper not stop? I have a file with all the links that it has visited in it, so it won't revisit a web page, but sometimes, when it has done a page recently, or it comes across a page with very little links, it will stop. Could you recommend a way to fix this?

---

### Post by Bodsda on 2011-11-30
> **CoffeeRain said:**
> Thanks! It's working much better now. Another question... Is there a way to make the scraper not stop? I have a file with all the links that it has visited in it, so it won't revisit a web page, but sometimes, when it has done a page recently, or it comes across a page with very little links, it will stop. Could you recommend a way to fix this?

Im sure we could.... we're gonna need to see all the code though.

Bodsda

---

### Post by CoffeeRain on 2011-11-30
OK, here it is, but it is rough and could be confusing.

```
import urllib
import re
import time
import sys

file = open('~/Desktop/emails.txt', 'a+')
filer = open('~/Desktop/emails.txt', 'r')
all = open('~/Desktop/scraper/emails.txt', 'r')
linkfile = open('~/Desktop/links.txt', 'a+')
linkfiler = open('~/Desktop/scraper/links.txt', 'r')
links = []
emails = []
foundemails = []
foundemails2 = []
global page
page = sys.argv[1]

if page[:7]!='http://':
  page='http://' + page


def GetLinks(webpage):
  try:
    f = urllib.URLopener().open(webpage)
    content = f.read()
    link = re.findall('<a href=".*"', content)

    for item in link:
      if item == '<a href=""':
        link.remove(item)
      else:
        item = re.findall('=".+"', item)
        item = item[0]
        item = item[2:-1]
        item = re.findall('http.*?"', item)
        if item == []:
          del item
        elif re.findall('\)', item[0]):
          try:
            link.remove(item)
          except ValueError:
            pass
        else:
          item = item[0]
          item = item[:-1]
          links.append(item)
  except IOError:
    pass



def GetEmails(webpage):
  try:
    f = urllib.URLopener().open(webpage)
    content = f.read()
    email = re.findall('[a-zA-Z0-9+_\-\.]+@[0-9a-zA-Z][.-0-9a-zA-Z]*\.[a-zA-Z]+', content)
    email = list(set(email))
    alllist = re.findall('.+\n', all.read())
    another = re.findall('.+\n', filer.read())
    for item in another:
      foundemails.append(item)
    for item in alllist:
      foundemails.append(item)
    for item in email:
      if item in foundemails:
        email.remove(item)
      elif item[-4:]=='.jpg':
        email.remove(item)
      else:
        foundemails.append(item)
        file.write(item + '\n')
        print item + "\t" + time.asctime(time.localtime())

  except IOError:
    pass

file = open('~/Desktop/emails.txt', 'a+')
GetLinks(page)
linkfile.write(page + '\n')
for item in links:
  if re.findall(page, linkfiler.read()):
    links.remove(item)
  global page
  page = item
  linkfile=open('~/Desktop/links.txt', 'a+')
  linkfile.write(page + '\n')
  file = open('~Desktop/emails.txt', 'a+')
  GetEmails(page)
  GetLinks(page)
  file.close()
  linkfile.close()
  for link in links:
    if link==item:
      links.remove(link)
    if link[-4:] == '.jpg' or link[-4:] == '.gif' or link[-4:] == '.png':
      links.remove(link)
```

---

