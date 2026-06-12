---
title: "[SOLVED] Scribus: How do I get Aspell to work?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by ciborium on 2008-11-01
At work I use Adobe Quark for a magazine publication.

After having put Ubuntu on my home PC, I found a very nice publishing program called Scribus, that works similarly.  

The only problem is that it doesn't appear to have a native spell checker.  

I found [THIS PAGE](http://wiki.scribus.net/index.php/Aspell_in_1.3.5svn") which explains how to compile Aspell into Scribus, but I think it only works when you are compiling Scribus.  

I already have Scribus and Aspell installed, and don't know much about compiling.  How do I just get Scribus to recognize that Aspell is there?  Or what other way is there to implement spell-checking into Scribus?

---

### Post by swisscow on 2008-11-01
Don't know about Aspell but I have just put together a 30 page magazine full of articles from the students I teach. I converted all their word doc files into open office files then just right clicked on a text box in scribus and chose get text, and imported the text. 

Used the spell check in openoffice to do the spelling work before the import.

Hope it helps

---

### Post by ciborium on 2008-11-01
Thanks, I was hoping for a fix, but a work-around will do!

---

### Post by Luca Borrione on 2012-09-30
You can type from terminal:
```
aspell --lang=en --encoding=utf-8 --mode=sgml --add-sgml-check=ch check your_document.sla
```

Reference:
[Scribus Wiki: Spell checking your Scribusdocument]("http://wiki.scribus.net/canvas/Spell_checking_your_Scribus_document")

---

### Post by overdrank on 2012-09-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

