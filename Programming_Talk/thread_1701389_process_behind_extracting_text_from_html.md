---
title: "process behind extracting text from html"
date: 2011-03-06
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-03-06
I was wondering what the logic/process behind any text-from-html extractor is?

---

### Post by Portmanteaufu on 2011-03-06
> **flyingsliverfin said:**
> I was wondering what the logic/process behind any text-from-html extractor is?

There are a variety of approaches to this, and which one you might pick depends heavily on a number of factors. How complex is the HTML being read? What would you like to do with the text once you've pulled it out? What are your speed / scaling requirements for the problem? Is the HTML locally stored, or would you be pulling down web pages?

A generic solution would be to use an HTML parsing library that would do the heavy lifting for you. Such libraries exist in most languages, and allow you to programmatically ask for things like "The text in the third set of <li> tags." However, if the text you're looking for is small and simple, loading up such a library might be overkill.

Could you narrow your question a bit?

---

### Post by flyingsliverfin on 2011-03-06
I guess for me it would be enough to know the simplest program would do it. I've only written one script so far that needs this kind of thing, but it sparked my interest a little on parsing html.

My program gets definitions (from a certain site) for a word you input.
The way i was doing it was find a pattern of tags in line X, then take all the text until "<". It works (mostly), but it feels a lot like brute-forcing a math problem and isn't elegant at all :)  

That lead me to wonder how the actual built-in ones do it... just the logic.

---

### Post by Portmanteaufu on 2011-03-06
Sounds like a fun script. :D

```

import urllib # Library that does web page requests
# Request a given web page
page = urllib.urlopen("http://dictionary.reference.com/browse/example")
# Read the entire web page's html into a variable
page_html = page.read()
page.close()

```

At that point, page_html contains the page's source code. You can use a library like [BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/documentation.html") to handle all the actual HTML parsing.

If you had another language of choice, let me know.

---

### Post by flyingsliverfin on 2011-03-07
Came in handy for my english vocab hw :) just fed the list into the program and it defined most of them for me

But the point of me asking here wasnt to find a better way to do it, but to learn how the better ways do it themselves.. sorry if i wasn't clear enough

WOW... thats a lot of documentation.. don't have that time right now :( (sleep, school, hw, tennis team etc)

can it find all the text that the user will see?

PS: i'd actually used merriam-webster.com (my friends had a big argument over what "real" english words are and what aren't)
Then i adapted my program to do translations to/from spanish using merriam-webster's translator... hadn't realized dictionary.com had one too

---

### Post by Portmanteaufu on 2011-03-08
> **flyingsliverfin said:**
> 
But the point of me asking here wasnt to find a better way to do it, but to learn how the better ways do it themselves.. sorry if i wasn't clear enough


Hrm -- I'm not sure I understand what you're asking. Could you try to be a little more specific?

[QUOTE=flyingsliverfin]
can it find all the text that the user will see?
[/QUOTE]

The short answer is "no". Without writing a pretty complicated program that could take in the html/css/javascript of a web page and determine everything that would be visible, there's no straightforward mechanism for knowing exactly what the user will see. This is one of the hazards of pulling text from a web page (a process sometimes called "Screen scraping"). Typically you have to look at the source code for a page and figure out where in the document the information normally appears and write a parser that will pull out whatever text is there. However, because the person running the website isn't supporting your efforts, there's no guarantee that they won't change the layout of the document several times a day. For that reason, screen scrapers take quite a bit of upkeep to stay relevant.

Depending on which website you're trying to pull information from, though, you might be able to find an [API]("http://en.wikipedia.org/wiki/Application_programming_interface") to let you interact with their system without using the web page front end. APIs rarely change because the site creators know that there are people relying on them. They also provide their information in an easy-to-read format like XML or JSON. Take a look at [this website]("http://www.programmableweb.com/") -- it provides a pretty thorough listing of web sites that have such interfaces.

---

### Post by flyingsliverfin on 2011-03-08
oh ok thanks the second answer is what i was looking for :)

---

