---
title: "Python interact w/ website"
date: 2007-11-27
forum: Programming Talk
---

### Post by Nekiruhs on 2007-11-27
How would I make a script in Python to interact with a javascript page? Specifically, it needs to activate a radiobox and a button. The site below has a generator of Freerice.org that works similarly to what I am trying to do, but I can't understand the code.

[http://smokyflavor.wikispaces.com/RiceMaker](http://smokyflavor.wikispaces.com/RiceMaker)

---

### Post by 11hjpphty76lkjj on 2007-11-27
I'm not 100% but I think that ruby on rails can do this?  Not sure if python can or can not.  but pretty sure that ruby can.

Hope this helps..

---

### Post by Wybiral on 2007-11-27
You probably don't want to make it "click" things on the page, you want it to submit data as a request. Look at the page and see how the form is being submitted.

---

### Post by ssam on 2007-11-27
[http://docs.python.org/lib/node578.html](http://docs.python.org/lib/node578.html) shows how to do GET and POST HTTP actions in python.

there are programs that let you simulate using websites, but they are mostly designed for testing sites. [http://en.wikipedia.org/wiki/Selenium_(software](http://en.wikipedia.org/wiki/Selenium_(software))

---

### Post by nanotube on 2007-11-28
hey
well, i wrote ricemaker, so i can tell you how it works :)

basically, i get the page, parse the sourcecode for the elements i need using beautifulsoup, and then create a POST request and do a urllib2.urlopen() with it.

so basically, look at your target page sourcecode, see what form elements you need to submit to where, and do a urllib2.urlopen() with first argument being the url, second argument being a urlencoded dictionary of your POST data.

another alternative is to use the [http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/) module to automate browsing.

---

### Post by pmasiar on 2007-12-02
From Python you cannot interact with Javascript on the page - and it does not make much sense, AJAX is just to change how the page is presented to the  visitor, which is non-existent.

Instead, check what JS does, and issue the same action, using GET or POST, to target website.

---

