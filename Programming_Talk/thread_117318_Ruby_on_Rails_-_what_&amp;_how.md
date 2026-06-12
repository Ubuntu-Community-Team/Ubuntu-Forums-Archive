---
title: "Ruby on Rails - what &amp; how?"
date: 2006-01-14
forum: Programming Talk
---

### Post by Burgresso on 2006-01-14
Hi everyone.

I'm curious about Ruby on Rails - and have questions I was hoping the ubuntu community could help me with. 

Although I have heard it's more of a mac thing, can it be developed on Ubuntu? If so, what do I need/need to do? For example, do I need a specific editor (like Quanta+ for web or PHP)? And what do I need to download? I'd be interested in playing with Ruby On Rails for web development.

Thanks in advance!

Burgresso

---

### Post by oakz on 2006-01-14
try this article for a nice intro to Ruby on Rails:
[http://www.onlamp.com/pub/a/onlamp/2005/01/20/rails.html](http://www.onlamp.com/pub/a/onlamp/2005/01/20/rails.html)

(yes you can develop RoR on Linux, or a Mac, or Windows...)

---

### Post by pertti on 2006-01-14
[This page]("https://wiki.ubuntu.com/RubyOnRails") in the Ubuntu Wiki which explains how to install it using RubyGems instead of apt-get, so you'll have the latest version.

---

### Post by pertti on 2006-01-15
Speaking of editors, you can use a lot of them. Most editors highlight ruby code, and some of them also highlight rhtml (ruby embedded in html). I played a bit with RoR using vim, which does understand rhtml using [this script]("http://www.vim.org/scripts/script.php?script_id=403").

There's also a plugin for [Eclipse]("http://www.eclipse.org") called [RadRails]("http://www.radrails.org"), which looks great, but I haven't used it yet.

---

### Post by Burgresso on 2006-01-17
Thanks everyone!

---

### Post by viscount on 2006-01-17
Emacs also has great highlighting support and auto tab completion
among other nicetys.

Ruby is a lot of fun. Great community.

---

### Post by gord on 2006-01-17
don't forget [django](http://www.djangoproject.com/), its like ruby on rails but designed for python and with slightly diffirent design phylosophys so it has some diffirent stuff.

---

### Post by dudus on 2006-02-06
[QUOTE=Burgresso]Hi everyone.
Although I have heard it's more of a mac thing, can it be developed on Ubuntu? If so, what do I need/need to do? For example, do I need a specific editor (like Quanta+ for web or PHP)? And what do I need to download? I'd be interested in playing with Ruby On Rails for web development.
Burgresso[/QUOTE]

Forget about this mac thing. Total mistake.

The language is interpreted so could be developed and deployed on any system that has the interpreter, wich includes ubuntu.

I strongly recomend you not to install rails from apt but to follow the [wiki]("https://wiki.ubuntu.com/RubyOnRails").

From the repos you'll only need the ruby(1.8) interpreter.

cheers

---

