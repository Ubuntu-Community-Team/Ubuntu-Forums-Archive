---
title: "Pulling guild roster from WoW armory"
date: 2007-08-30
forum: Programming Talk
---

### Post by er76 on 2007-08-30
Anyone give some suggestions on pulling a list from one website to another website.

For example pulling a guild roster from [www.wowarmory.com](www.wowarmory.com)

---

### Post by pmasiar on 2007-08-30
I am not sure if I understand, but IMHO what you want to do is:
- fetch a web page
- parse it for some information
- store it somewhere else

What is your programming background? Are you willing to learn, or you want someone to create script for you? What did you tried? What was obstacles you encountered?

Read [How To Ask Questions The Smart Way](http://catb.org/~esr/faqs/smart-questions.html)

---

### Post by CptPicard on 2007-08-30
Just off the top of my head without looking at the case more closely, I'd write a shell script where I **wget** the original, use **sed** to rewrite the other html into "my" html, and then upload the end result to my server using the tool of my choice, whichever it is.

Another possibility for the fetching and rewriting bit is using a programming language, like Python.

---

### Post by skeeterbug on 2007-08-30
> **er76 said:**
> Anyone give some suggestions on pulling a list from one website to another website.

For example pulling a guild roster from [www.wowarmory.com](www.wowarmory.com)


I do this on my site ([www.guildreport.com](www.guildreport.com)). Not to pull the entire roster, but to check if the guild exists and if it is the right faction. I used Python's urllib to fetch the page, and had to use a regex to parse some javascript code (the faction is put in via javascript). However, this was somewhat wrong of me to do. The armory already uses XML files for the data, and an XSLT stylesheet to translate it to HTML. 

My question is, is there a way to get the XML with urllib so it doesn't perform the translation (when I view source in FireFox it shows me the XML, not the HTML).

---

### Post by pmasiar on 2007-08-30
> **skeeterbug said:**
> I use a regex to parse some javascript code 

You may want to look at ElementTree (included in core since Py2.5) - **much** nicer XML parser

---

### Post by skeeterbug on 2007-08-30
edit:

---

### Post by skeeterbug on 2007-08-31
edit: removed

---

### Post by er76 on 2007-09-01
I know how to program.  I am exploring my options to see what is the best method of doing this task.

---

### Post by skeeterbug on 2007-09-06
> **er76 said:**
> I know how to program.  I am exploring my options to see what is the best method of doing this task.

Way to come out and be an ******* when people were trying to help you explore those ideas. My code served as a proof-of-concept, not to teach you how to program.

---

### Post by er76 on 2007-09-08
I was replying to the first reply, not trying to be a jerk.

---

### Post by pmasiar on 2007-09-08
> **er76 said:**
> I was replying to the first reply, not trying to be a jerk.

I like when people trim replies :-) , but if you trim all out, it is not obvious to which comment you responded.

BTW "I know how to program" does not say much about your skill level. If you know it all, you would not be asking for help, or would you?

---

### Post by alisiel on 2008-02-27
> **skeeterbug said:**
> 
My question is, is there a way to get the XML with urllib so it doesn't perform the translation (when I view source in FireFox it shows me the XML, not the HTML).
Has anyone found a way to do this yet?
Thanks

---

### Post by neuromancer2701 on 2008-06-01
It is pretty easy to pull info from the wow armory. Python is the way to go. I have a background in embedded C and I picked up python enough to pull my guild's gear from the armory. 
I used both of the modules mentioned already.
ElementTree
urllib

Here is my [writeup]("http://jerdking.blogspot.com/2008/05/scraping-wow-armory-with-python.html")
Here is another [guys]("http://www.petersblog.org/node/1408") that I found helpful.

To get your guild roster use the link below with 
R as your Realm and n as your guild name.
[http://www.wowarmory.com/guild-info.xml?r=&n=](http://www.wowarmory.com/guild-info.xml?r=&n=)

Hope that helps.

---

### Post by slavik on 2008-06-02
look at my username and you know what I am going to say. :)

HINT: Perl!!!

---

