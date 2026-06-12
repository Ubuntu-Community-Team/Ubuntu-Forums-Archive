---
title: "Python help"
date: 2007-08-21
forum: Programming Talk
---

### Post by cmat on 2007-08-21
I'm looking for a way to take a few lines of text from a web page and display them in the console.

---

### Post by pmasiar on 2007-08-21
... and which part is causing you a problem? Use module urlib or urllib2 to fetch a page, parse it, and print. Child's game :-)

---

### Post by cmat on 2007-08-21
the parsing part. I need to read a single line and remove all the HTML code around it. Just displaying the text in the console. 

As a test we could try to read the copyright notice at the bottom of google's homepage. I've never did parsing before and I don't know where to start.

---

### Post by cmat on 2007-08-22
I'm guessing after the page is stored as a string. You use the readline() function to find the line and then split that off from the rest of the string. However it doesn't seem to be working for me. Or I'm not using it for it's intended purpose. I'm a serious noob to anything other than mathematical work with programming.

---

### Post by triptoe on 2007-08-22
```
import urllib



f=urllib.urlopen('http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345").read()

print f

```

Thats how i did it....

---

### Post by ssam on 2007-08-22
```
import urllib

f=urllib.urlopen('http://google.com/")
for line in f:
    print line

```

now you can process each line of html individually

for example you could filer on lines containing a copyright symbol
```

for line in f:
    if "&copy;" in line:
        print line

```

then use sting manipulation to chop out the bits you want. [http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html) has a list of methods fro strings.

for more advanced stuff there are other methods.
if the web pages is clean xhtml (the google home page has [50 errors]("http://validator.w3.org/check?uri=http%3A%2F%2Fgoogle.com%2F&charset=%28detect+automatically%29&doctype=Inline&group=0")) then you can use an XML library.

for invalid pages, there is [Beautiful Soup]("http://www.crummy.com/software/BeautifulSoup/")

---

### Post by pmasiar on 2007-08-22
readlines() reads all lines from a file, so to make one big text string (from file fetched by urllib, joined by ''): 

fulltext = ''.join(open('file.name').readlines())

---

### Post by cwaldbieser on 2007-08-22
> **cmat said:**
> the parsing part. I need to read a single line and remove all the HTML code around it. Just displaying the text in the console. 

As a test we could try to read the copyright notice at the bottom of google's homepage. I've never did parsing before and I don't know where to start.

You can use HTMLParser in section 13.1 of the standard library for parsing the data.

---

### Post by cmat on 2007-08-22
You guys are awesome thanks, I'll post any other questions I have.

---

### Post by cmat on 2007-08-22
Okay I got finding the script finding the line, but there must be an easier way to easier way to remove the HTML tags. Instead of the[FONT="Courier New"] replace("</font>", "")[/FONT] for every kind of tag.

---

### Post by pmasiar on 2007-08-22
split() out the parts you need - even in multiple steps

---

### Post by ssam on 2007-08-22
> **cmat said:**
> Okay I got finding the script finding the line, but there must be an easier way to easier way to remove the HTML tags. Instead of the[FONT="Courier New"] replace("</font>", "")[/FONT] for every kind of tag.

you could look at regular expressions.

---

### Post by pmasiar on 2007-08-22
yes he could, but re module is last defense, not the first :-)

---

### Post by ssam on 2007-08-22
> **pmasiar said:**
> yes he could, but re module is last defense, not the first :-)

true they are slow and ugly. but for people who are familier with them they get the job done.

---

### Post by pmasiar on 2007-08-22
> **ssam said:**
> for people who are familier with them they get the job done.

... which obviously is not the case of OP :-)

---

### Post by cmat on 2007-08-23
Certainly I've never done anything like this since I was using VB.

---

### Post by triptoe on 2007-08-23
why are regular expressions last defense? just curious

---

### Post by ghostdog74 on 2007-08-23
> **triptoe said:**
> why are regular expressions last defense? just curious

because most of the stuff we do can be done just by Python's string manipulation functions..unless its very very complex....

---

### Post by DirtDawg on 2007-08-23
Isn't there a simple way to replace 
```
 replace("</font>", "") 
```
with a wildcard character? Like
```
 replace("<*>", "") 
```
This is obviously not correct, but it couldn't be too much more difficult than that, could it?

I've also been advised to avoid regular expressions. I think the quote was something like "A student decides to solve a problem with regular expressions. Now she has two problems!"

---

### Post by ghostdog74 on 2007-08-23
if replace() can't do the job (which it really doesn't) , then its all up to your imaginatoin...here's a very simplistic example....
```

s="<font>test</font><br>"
while 1:
    if "<" in s or ">" in s:
        openind=s.index("<")
        closeind=s.index(">")
        s = s.replace(s[openind:closeind+1],"")        
    else:
        break
print s

```
the idea is to get the position of where < and its corresponding > are, then use string slicing to perform the "replace"..however, its just simplistic, you have to adapt to your situation..

---

### Post by cwaldbieser on 2007-08-23
> **cmat said:**
> Okay I got finding the script finding the line, but there must be an easier way to easier way to remove the HTML tags. Instead of the[FONT="Courier New"] replace("</font>", "")[/FONT] for every kind of tag.

The following is a pretty simplistic approach to outputting the text from the markup.
```

import htmllib, formatter

awriter = formatter.DumbWriter()
aformatter = formatter.AbstractFormatter(awriter)
parser = htmllib.HTMLParser(aformatter)

#Load example web page data.
f = file("index.html", "r")
data = f.read()
f.close()

parser.feed(data)
pareser.close()

```
Note that there are utilities like html2text that also can make short work of this sort of task.

---

### Post by pmasiar on 2007-08-23
You used non-greedy '.*' pattern, but regex uses greedy "death-star" :-) which causes common problems BTW. So:
closeind = s.rindex('>') # find **last** closing >

---

