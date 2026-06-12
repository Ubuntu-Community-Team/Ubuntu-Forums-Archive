---
title: "[python]beginner trying to get data from websites"
date: 2009-11-09
forum: Programming Talk
---

### Post by Xender1 on 2009-11-09
Just wondering what the best way to start learning this is, I really have no idea. I want to start learning how to use python to retrieve data from websites. Is CGI the right direction to go? Thanks in advance.

---

### Post by diesch on 2009-11-09
CGI is an interface to create dynamic webpages using different programming languages. 

To retrieve data from webpages have a look at [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/) (package python-beautifulsoup)

---

### Post by ghostdog74 on 2009-11-09
BeautifulSoup doesn't really retrieve data from website. Its a HTML parser. unless of course BS has improved so much so that now it acts as a web crawler. Otherwise, use HTTP libraries such as urllib2, urllib and httplib (others may include cookielib etc ).

---

### Post by diesch on 2009-11-09
In most cases you need a HTML parser to retrieve data from websites.

---

### Post by Bjalf on 2009-11-09
I used about a month to write my first python script (to download web comics). I had never used python before, and I just learnt as I went ahead. Notepad++ on one screen, docs.python.org on the other. And a handfull of e-books, like "Python Cookbook", "Python Programming for the Absolute Beginner", stuff like that.

The script reads a page from the web, searches through it with regular expressions, and then downloads the comic before going to the next page. Libraries I used: os, urllib2, time, calendar, string, re, fnmatch, tempfile, robotparser, random. I wrote my own INI file handler, because it was simpler than trying to understand ConfigParser  ](*,)

I had great fun implementing local static variables, which doesn't exist in Python  8-)

For my next project, maybe I'll try some of that new-fangled Object Oriented Programming.

:p

---

### Post by spupy on 2009-11-09
> **Bjalf said:**
> I used about a month to write my first python script (to download web comics). I had never used python before, and I just learnt as I went ahead. Notepad++ on one screen, docs.python.org on the other. And a handfull of e-books, like "Python Cookbook", "Python Programming for the Absolute Beginner", stuff like that.

The script reads a page from the web, searches through it with regular expressions, and then downloads the comic before going to the next page. Libraries I used: os, urllib2, time, calendar, string, re, fnmatch, tempfile, robotparser, random. I wrote my own INI file handler, because it was simpler than trying to understand ConfigParser  ](*,)

I had great fun implementing local static variables, which doesn't exist in Python  8-)

For my next project, maybe I'll try some of that new-fangled Object Oriented Programming.

:p

That was also one of my projects while learning python. :) I wrote a script that "scrapes" manga (whole one or single chapters) from a website. Although I don't read manga, it was a fun project. The modules involved are: commands, urllib2, re. The most tedious part is writing the regular expressions to extract URLs of the next pages.

---

### Post by ghostdog74 on 2009-11-09
> **diesch said:**
> In most cases you need a HTML parser to retrieve data from websites.
HTML parser is just html parser, it parses html. BSoup is one of them. To retrieve data from website, the common library to use is urllib2 and urllib. AFAIK, BS doesn't retrieve web pages. All it does is parse HTML unless BSoup is now improved  to fetch web pages as well..

---

### Post by dracule on 2009-11-10
> **ghostdog74 said:**
> HTML parser is just html parser, it parses html. BSoup is one of them. To retrieve data from website, the common library to use is urllib2 and urllib. AFAIK, BS doesn't retrieve web pages. All it does is parse HTML unless BSoup is now improved  to fetch web pages as well..

is it so hard to do:

parsed  = BeautifulSoup(urllib2.open("http://google.com"))

?

lol. 

If you need to, you can use "Mechanize". It is a library which will go through and allow you to crawl a webpage. You can easily go through all the links, submit forms, and has functions such as "back" and "forward" like a normal browser (but this isnt a browser).

---

### Post by ghostdog74 on 2009-11-10
> **dracule said:**
> is it so hard to do:

parsed  = BeautifulSoup(urllib2.open("http://google.com"))

that's not the point i am arguing. what you are doing is basics of passing arguments to function/methods/classes. Try doing the above without urllib2, ie only BS. do you get what i mean? If BS can do it without urllib2, then fine.  It shows that since the last time i used BS, it has improved alot so much so that now it can grab web pages and parse them on the fly as well.

---

### Post by dracule on 2009-11-10
> **ghostdog74 said:**
> that's not the point i am arguing. what you are doing is basics of passing arguments to function/methods/classes. Try doing the above without urllib2, ie only BS. do you get what i mean? If BS can do it without urllib2, then fine.  It shows that since the last time i used BS, it has improved alot so much so that now it can grab web pages and parse them on the fly as well.

what im arguing is that 1 line of code I dont really see as an "improvement". 
You could easily extend beautiful soup to do it on the fly if you wanted. 
```

class FlyInMySoup(BeautifulSoup):
      def __init__(self, url):
           BeautifulSoup.__init__(self, urllib2.open(url))
           self.location=url

```

I guess theoretically you could spend 5 extra minutes and make functions extending "a" tags to do things like "parsed.body.div.a.followLink()" or have a history to use "back()", etc. 

but I dont see what not using urllib2 is going to do. It is a standard python lib, and BS already uses several standard python libs.

---

### Post by Bjalf on 2009-11-11
This thread has degenerated into a BS argument.

[http://www.badum-tish.com/](http://www.badum-tish.com/)

:lolflag:

---

