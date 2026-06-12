---
title: "How to Write Program to Get Data from Web Page?"
date: 2006-06-06
forum: Programming Talk
---

### Post by Ubuntist on 2006-06-06
Although I've done lots of programming, it has always been very much numerical.  No interaction with the OS, no use of databases, no graphics,  Just straightforward number crunching.  Parameters and data read from and results written to plain old sequential-access files.

Now, however, I'd like to write a program that would get specific bits of data from a number of web pages.  Could someone please point me in the direction of how to get started.  What's a good language to use (Python? Ruby?)?  Within a suitable language is there a particular package I should make use of?  Are there any simple examples I could study?

---

### Post by debernardis on 2006-06-06
[QUOTE=Ubuntist]What's a good language to use (Python? Ruby?)?[/QUOTE]

Why not php? I have a php script online since 2002 on my site to get pages from the national library of medicine and reformat them in a simplified, pda-friendly way: [http://www.debernardis.it/medasq.php](http://www.debernardis.it/medasq.php)

The fopen function is your friend.

Now, I am no programmer at all, I am a medical doctor, but that works:
```

$open= fopen("http://www.myurl.com", "r");
$mystuff= fread($open, 5000000);
fclose($open);

```
(might be bad code but works indeed!)
Then with $mystuff you can do what you like 8-)

---

### Post by simplyw00x on 2006-06-06
Or python is pretty easy as well, and included in Ubuntu. Something like:
```
import urllib
page=urllib.urlopen("http://www.myurl.com/")
data=page.read()
```

---

### Post by Ubuntist on 2006-06-06
Thanks -- that's a big help.

It looks like the next step is to figure out how to parse the string representation of the webpage.  Are there any utilities for doing that built into Python (I happend to be more familiar with it that with PHP)?  In the Python docs I found something about HTML parsing, but I can't make sense of it.

2nd follow-up question: Some of the web content I want to reach requires choosing a selection and then clicking a "Go" button -- is there a way to do that?

---

### Post by ssam on 2006-06-06
parsing html can be tricky, there are plenty of xml parsing libraries that will work on xhtml, but they will raise an exception if the xml is not valid.

depending on how the html is wirten it might be good to split it into individual lines, or try and split it into tags. to grab all the urls from an array of lines something like
```

for this_line in lines:
    if this_line.startswith("<a href"):
        bits = this_line.split('"')
        print bits[1]

```
though you'd need somethingthing more complex if hrefs appeared part way though a line.

to submit a form you may not need to parse the html at all. you'll need to check if urllib can do GET and POST in a http request.

---

### Post by simplyw00x on 2006-06-06
[http://ubuntuforums.org/showpost.php?p=1102105&postcount=4](http://ubuntuforums.org/showpost.php?p=1102105&postcount=4) has links to some html parsers for python.

---

### Post by Ubuntist on 2006-06-06
Next stupid question: how do I know whether I'm dealing with HTML, STHML, XML, etc., and what's the difference, anyway?

---

### Post by ssam on 2006-06-06
i think you need to have a bit of a read around the subject. try these

[http://en.wikipedia.org/wiki/Http](http://en.wikipedia.org/wiki/Http)
[http://en.wikipedia.org/wiki/Html](http://en.wikipedia.org/wiki/Html)
[http://en.wikipedia.org/wiki/Xml](http://en.wikipedia.org/wiki/Xml)
[http://en.wikipedia.org/wiki/Xhtml](http://en.wikipedia.org/wiki/Xhtml)

and for more details see [http://www.w3.org/](http://www.w3.org/)

then remember that a lot of webpages deviate from the specifications. web browsers have a lot of code to handle broken html/xhtml. if you want to write a program that works for many web sites, it will take a lot of work.

if you just want to submit one form on one website, you will have much less work. but if they change the site layout you will have to change your code.

---

### Post by Ubuntist on 2006-06-06
Thanks ssam -- that's exactly what I needed!

---

### Post by UbuWu on 2006-06-06
This is probably a nice example of how you could do such a thing using python:
[http://www.oluyede.org/blog/2006/02/13/italian-tvguide-or-why-python-is-wonderful/](http://www.oluyede.org/blog/2006/02/13/italian-tvguide-or-why-python-is-wonderful/)

---

### Post by Ubuntist on 2006-06-13
Thanks, UbuWu -- BeautifulSoup does take a lot of the drudgery out of it.:)

---

