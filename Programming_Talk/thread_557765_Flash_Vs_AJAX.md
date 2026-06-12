---
title: "Flash Vs AJAX"
date: 2007-09-23
forum: Programming Talk
---

### Post by thenetduck on 2007-09-23
Well I am interested in what you think about Flash vs AJAX. As you know, AJAX has gained a lot of popularity recently. I have been implementing it on my website but noticed that with one of my programs you can't manipulate images without re-rendering the whole image (this is in AJAX) while in Flash it's not an issue. 

What are your thoughts? Will Flash be outgrown by AJAX ? or will AJAX continue to be the implementation of Javascript that makes cool effects on sites but no big online applications. 

I think AJAX in the future personally.

The Net Duck 

P.S. Does anyone out there have a solution to not have to render manipulated images kind of like Flash?

---

### Post by mssever on 2007-09-23
Flash and AJAX are good for different things. While I don't really know about the specific use case you cited, Flash seems to be the most portable way to play sounds and display video. However, Flash isn't open source, which is a limiting factor, and it's not well suited for most kinds of web applications, where it introduces serious accessibility problems. Also, AJAX works by manipulating the DOM, whereas Flash runs entirely in its own space. So Flash is  inherently limited.

I would recommend against Flash except in situations where it can be proven that Javascript (AJAX) can't adequately do the job.

EDIT: Oh, and Flash-based banner ads are evil. :)

---

### Post by pmasiar on 2007-09-23
Flash is direct competitor of Java Applets (which totally failed so far) and Silverlight. AJAX is about manipulation of DOM, which is changes in underlying HTML.

> no big online applications.

What about GMail? It is pretty big and clever, and it is AJAX. Same with google documents: office-like editor, and spreadsheet, in AJAX. Or calendar. They are pretty big, and AJAX-based. Most applications are about text, not pretty pictures, so Flash is not necessary unless try games. And for games, IMHO good old client is better solution.

---

### Post by Wybiral on 2007-09-23
> **pmasiar said:**
> What about GMail? It is pretty big and clever, and it is AJAX. Same with google documents: office-like editor, and spreadsheet, in AJAX. Or calendar.

Google uses AJAX all over (just look at some of their [API]("http://code.google.com/apis/")'s).

---

### Post by trwww on 2007-09-24
> **thenetduck said:**
> Well I am interested in what you think about Flash vs AJAX. As you know, AJAX has gained a lot of popularity recently. I have been implementing it on my website but noticed that with one of my programs you can't manipulate images without re-rendering the whole image (this is in AJAX) while in Flash it's not an issue. 

What are your thoughts? Will Flash be outgrown by AJAX?

AJAX and Flash are not mutually exclusive.

The only thing stopping you from doing AJAX in Flash is your experience. It works just fine and there are plenty of examples out on the web.

---

