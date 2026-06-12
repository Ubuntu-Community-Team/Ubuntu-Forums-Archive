---
title: "Ruby apps for linux"
date: 2008-12-21
forum: Programming Talk
---

### Post by dannytatom on 2008-12-21
I'm playing with Shoes, a Ruby GUI toolkit, and it's pretty neat.  I was gonna try and make a small linux app, but had a question.

Are there any pros/cons to using Ruby compared to all the other languages used for most linux apps (C, Python, etc)?

---

### Post by Sorivenul on 2008-12-21
Ruby is a fine, fun language.  The pros and cons will vary from language to language and also from project to project.

However, the ["Why Ruby?"]("http://www.ruby-doc.org/whyruby") article from the RubyDoc website may be of interest.

---

### Post by dannytatom on 2008-12-21
I'll look into the list on ruby-docs (quite a long one :P).  It's true that the pros and cons will vary, I guess my main concern is wether or not Ruby is worth learning.  

It does look like a good language, and from what I've played with so far, fun to write.  But is it fast/efficient/etc enough to use for desktop apps?

---

### Post by shadylookin on 2008-12-21
> **dannytatom said:**
> I'll look into the list on ruby-docs (quite a long one :P).  It's true that the pros and cons will vary, I guess my main concern is wether or not Ruby is worth learning.  

It does look like a good language, and from what I've played with so far, fun to write.  But is it fast/efficient/etc enough to use for desktop apps?

desktop apps usually spend a good deal of time waiting on user input rather than doing terribly intensive processing so speed shouldn't be a huge issue. I've never heard about ruby teaching bad habits so you shouldn't have any reason not to learn it if you want to

---

### Post by dannytatom on 2008-12-21
Ah, good then.  Thank ya.  :)

---

### Post by mssever on 2008-12-21
Ruby is one of my favorite languages. It's well worth learning. These days, though, I must admit that while I prefer Ruby in principle, I do write more Python--largely because Python has a lot more libraries, and Ubuntu's Ruby packages leave a bit to be desired.

But Ruby is definitely worth your time.

Incidentally, Net Responsibility (see my signature) is mostly in Ruby with a bit of Python thrown in.

---

### Post by dannytatom on 2008-12-21
Know of any good (e)books or sites?  Preferabbly ones with a bit of a personality to them.  I have a hard time keeping focused when it reads like an encyclopedia. ;o

I'm already checking out the Ruby and Shoes sites.  Also, should I start with Ruby on Rails, or would that hinder progress?

---

### Post by mssever on 2008-12-21
> **dannytatom said:**
> Know of any good (e)books or sites?  Preferabbly ones with a bit of a personality to them.  I have a hard time keeping focused when it reads like an encyclopedia. ;o

I'm already checking out the Ruby and Shoes sites.  Also, should I start with Ruby on Rails, or would that hinder progress?
If you want a Ruby book with personality, you can't beat [*Why's (poignant) Guide to Ruby*]("http://poignantguide.net/ruby/index.html"). It's unlike any programming book you've ever read. I promise.

When I was learning Ruby, the most helpful book was the [Pickaxe]("http://whytheluckystiff.net/ruby/pickaxe/"), but the version available online is a bit outdated. It's great for the basics, but don't rely on its API docs to be up-to-date.
[URL="http://tryruby.hobix.com/"]
Try Ruby[/URL] is a great little interactive tutorial, also written by Why.

The [official API docs]("http://ruby-doc.org/") will be indispensable, especially once you get a little experience. Keep this one bookmarked.

Finally, [here's a book]("http://www.infoq.com/minibooks/ruby/") that's also available free. I haven't read it, so I don't know whether it's any good.

EDIT: Rails is almost a different language because of all the metaprogramming that goes on. Same goes for Shoes. My opinion is that you should learn straight Ruby first. I haven't found any good documentation for Rails.

---

### Post by dannytatom on 2008-12-21
If I could thank you more than once I would.  That's a ton of helpful links.  Shoes seems a bit different than Ruby and I haven't really looked into Rails.

I got interested in Rails while reading about Shoes.  It loosk pretty easy to understand, but it seems like I'd get it a lot more if I already knew Ruby. :p

Anyway, thanks a bunch. :)

---

### Post by mssever on 2008-12-21
> **dannytatom said:**
> If I could thank you more than once I would.  That's a ton of helpful links.  Shoes seems a bit different than Ruby and I haven't really looked into Rails.

I got interested in Rails while reading about Shoes.  It loosk pretty easy to understand, but it seems like I'd get it a lot more if I already knew Ruby. :p

Anyway, thanks a bunch. :)
Ruby is a very dynamic language, and you can modify the language itself at runtime. Both Shoes and Rails do that extensively. It's great in that it allows you to get stuff done with minimal code. The downside is that there's a lot more to learn before you cen get up to speed.

Incidentally, I've never messed with Shoes, and my past attempts to learn Rails were thwarted by lack of web-based documentation and my unwillingness to spend money on a real book. So I actually don't use Ruby in the situations where it's most famous.

---

### Post by dannytatom on 2008-12-21
Main thing that attracted me was that you can use it as a web framework and for desktop apps.  That and, compared to the only other languge I (kinda) know (PHP), it's a lot more readable.

Also, I'm liking this Try Ruby thing. :)

---

### Post by mentallaxative on 2008-12-22
Oooh, a thread about Ruby....

I really like Ruby. I started with Python, which was okay, but I kinda lost the plot when it came to OO programming in it. I went and tried Ruby and since then I've picked up a lot of concepts that I found difficult to understand in Python.

Shoes is pretty fun. However, I'm not really sure what sort of useful app you can make out of it besides games. The Shoes website has a section called the Shoebox with some example apps.

mssever: I have the same thoughts as you; Ruby just fits me better, but since Python is everywhere one can't escape writing some stuff in it.

---

### Post by dannytatom on 2008-12-22
I just finished **Try Ruby**, and reading **Why's (poignant) Guide to Ruby** right now.  This has to be the easiest-to-understand guide to a language I have ever read.

& yeah, there were a couple things in the shoebox that seemed nice (A couple twitter apps, and some youtube downloaders).  None were amazing on their own, but it showed potential.

---

### Post by Greyed on 2008-12-22
> **dannytatom said:**
> It does look like a good language, and from what I've played with so far, fun to write.  But is it fast/efficient/etc enough to use for desktop apps?

This is a recurring discussion here in the PT subsection of UF.  I've not really dabbled in Ruby but have worked extensively in Python.  The answer to this question is that it depends on your application.  However, for large swaths of development these days the popular scripting languages, regardless of personal preference, are sufficiently fast to idle with the best of them.  Write the app in the dynamic language of choice and if the performance portions are too slow then look at rewriting those portions in a lower level lanauge to leverage the best of both worlds.

IE, it is better to quickly write slow clode and slowly write optimizations for the the parts that need it than to slowly write optimized code for all portions, including the 90-99% that doesn't need it.  ;)

---

### Post by mssever on 2008-12-22
> **mentallaxative said:**
> Oooh, a thread about Ruby....

I really like Ruby. I started with Python, which was okay, but I kinda lost the plot when it came to OO programming in it. I went and tried Ruby and since then I've picked up a lot of concepts that I found difficult to understand in Python.

Shoes is pretty fun. However, I'm not really sure what sort of useful app you can make out of it besides games. The Shoes website has a section called the Shoebox with some example apps.

mssever: I have the same thoughts as you; Ruby just fits me better, but since Python is everywhere one can't escape writing some stuff in it.
Yes, some things, such as OO, are just natural in Ruby. I didn't really learn OOP until I learned Ruby, then it seemed so easy I couldn't figure out why I had trouble earlier. Python's a bit of a mixture, and IMHO not the best language to learn OOP in. However, Python is much more popular and has much better standard library coverage,* so I often end up using Python instead of Ruby. Library coverage is huge for me.


* As far as standard libraries go, the only place I know of where Ruby beats Python is YAML, which is part of the Ruby stdlib, unlike Python.

---

