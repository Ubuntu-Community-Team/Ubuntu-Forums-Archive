---
title: "storing text in a db"
date: 2010-01-03
forum: Programming Talk
---

### Post by badperson on 2010-01-03
Hi,
I was curious how this and other similar forums store text in the db tables. 

I'm going to guess that the entry I'm typing is stored as text, and that if I add any **emphasis tagging** the bracketed tags will also be stored as text...but when i searched for "[B]" I didn't get any hits. 

I've asked about this issue before, and I think the new mysql xml features are the best way to go, but was curious as to how other apps are structured. 

thanks, 
bp

---

### Post by Some Penguin on 2010-01-03
Is there a reason you're not mentioning what database you're using, not showing any sample input, and not showing any of the commands you're using to actually parse the sample input and store it into the database?

---

### Post by badperson on 2010-01-03
Hi,
the reason is that I'm interested in what the standard is for a lot of these popular php/mysql type forums (I'm guessing that's what the ubuntu forums is). 

I'm starting to write a similar app for myself, and for more narrative type data, I find it awkward to use plain text. It seems a lot more intuitive to me to use xml and to have the servlet render it as html via an xslt stylesheet. 

I know that mysql has some basic xml/xpath functionality, not a full blow xml db, though...and I've used that a bit. 

So I guess I was asking the question from more of a standard practices standpoint. 

Curious if others on the forum have built these types of apps and how you went about it. 
thanks!
bp

---

### Post by Hellkeepa on 2010-01-03
HELLo!

Your question is somewhat open ended, and covers a huge area of knowledge. Parts of which does not have a definitive answer, but is totally dependant upon what kind of functionality you're looking for in your forum software.

Generally speaking, there are at least 2 tables in play: One for storing the thread data, and one for storing the post data. The posts themselves are, as you correctly assumed, in TEXT fields. The other data, as PosterID, date, post ID, thread ID and such is stored in their applicable field type.
The thread table usually contains thread ID, thread title, and perhaps other meta-data associated with the thread itself.

The second part of your question, where you're asking about how the forum tags are stored and processed. I recommend searching for "bbcode script php" online, you'll find a lot of resources and finished scripts if you do.
Here's is one example: [http://norskwebforum.no/viewtopic.php?f=50&t=25952](http://norskwebforum.no/viewtopic.php?f=50&t=25952) (scroll down a bit)

However, if you really want to learn how a forum is built up. Then there's just one thing you can do: Install a couple of the different free forum systems out there, and study them in detail. The big ones, like phpBB 3, are massive though. So expect to spend many days, if not weeks, before you're able to grasp them fully.

Happy codin'!

---

