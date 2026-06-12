---
title: "Does this exist?  A standalone client for forums"
date: 2009-08-10
forum: Programming Talk
---

### Post by skullmunky on 2009-08-10
I've noticed I spend a lot of time on dozens of different forums.  The "forum" idea seems to be replacing Usenet, but it lacks anything like a centralized reader so you can quickly browse all the forums you read and all the threads you're participating in.  Is there anything like that?  Would other people find that useful?  Is it even feasible?

---

### Post by Muboo on 2009-08-10
AFAIK, it doesn't exist yet. However, it is feasible by parsing HTML code (most likely from simplified version of pages), but not directly from the server.

---

### Post by tgalati4 on 2009-08-10
Most forums have RSS feeds, so you could subscribe to the subforums that interest you most and organize the RSS feeds in a way that makes sense to you.  You can set the preferences on the readers to grab just the headers of new posts or xx number of lines.

---

### Post by andrew.46 on 2009-08-23
Hi skullmunky,

> **skullmunky said:**
> The "forum" idea seems to be replacing Usenet

The death of Usenet has been predicted many, many times...

Andrew

---

### Post by nvteighen on 2009-08-23
Hm... I guess forums were designed with web browsers in mind, so the tool seems to be the web browser itself.

Maybe a plugin for Firefox could help with some stuff... But I'm not sure...

---

### Post by Joeb454 on 2009-08-23
I suppose you could use [prism]("http://labs.mozilla.com/prism/") and have each forum mimick a standalone application :)

Other than that, I don't think one exists, except tabbed browsing.

---

### Post by madnessjack on 2009-08-24
> **Joeb454 said:**
> I suppose you could use [prism]("http://labs.mozilla.com/prism/") and have each forum mimick a standalone application :)

I'd recommend using Chrome's application shortcut feature. I use it at work for the CMSs I use everyday and it's seamless, pain free and super fast. :-P

---

### Post by WitchCraft on 2009-08-24
> **skullmunky said:**
> I've noticed I spend a lot of time on dozens of different forums.  The "forum" idea seems to be replacing Usenet, but it lacks anything like a centralized reader so you can quickly browse all the forums you read and all the threads you're participating in.  Is there anything like that?  Would other people find that useful?  Is it even feasible?

You can use gtk webkit or wxWebkit to embed a browser window in your application.

Then, on the left side you'd have something like a list of forums.
I wouldn't recommend having the list in the browser in a frame because there are always people who think they have to disable frames on their webpage.

---

### Post by Cracauer on 2009-08-24
It's really time that these forums separate content and presentation. All the posts and threads should come as XML.

Problem is that this will kill the ads, so...

---

### Post by madnessjack on 2009-08-25
> **Cracauer said:**
> It's really time that these forums separate content and presentation. All the posts and threads should come as XML.

[http://en.wikipedia.org/wiki/HTML_5](http://en.wikipedia.org/wiki/HTML_5)
HTML5 (or the XML version at least) should have these standards in place already. Surely then it's just a case of getting a program to parse them.

---

### Post by Cracauer on 2009-08-25
> **madnessjack said:**
> [http://en.wikipedia.org/wiki/HTML_5](http://en.wikipedia.org/wiki/HTML_5)
HTML5 (or the XML version at least) should have these standards in place already. Surely then it's just a case of getting a program to parse them.

I don't want HTML in XML.

What I need is an actual DTD for discussion forums, with tags for individual posts, threads, dates, author, body etc.

---

### Post by johnl on 2009-08-25
> **WitchCraft said:**
> You can use gtk webkit or wxWebkit to embed a browser window in your application.

Then, on the left side you'd have something like a list of forums.
I wouldn't recommend having the list in the browser in a frame because there are always people who think they have to disable frames on their webpage.

I've mocked this up for you :)


[img]http://ubuntuforums.org/attachment.php?attachmentid=126263&stc=1&d=1251253141[/img]

---

### Post by skullmunky on 2009-08-26
:) nice mockup.  Ok, maybe I'll start fooling around with this.  Just having the list of forums is ok, but the real thing I'm interested in is separating out all the threads I'm interested in following from a bunch of different forums.  Like how this one has the "show all your threads" and "show all your posts"?  like that but cross-forum.

---

### Post by madnessjack on 2009-08-26
> **Cracauer said:**
> I don't want HTML in XML.

(XHTML5) has pros and cons, pros being it's already a standard but that's not why I'm a strict XHTML user. I do it because it forces me to keep things in order. If I went back to the HTML4 style of things my laziness would get the better of me.

> **johnl said:**
> I've mocked this up for you :)
Joking aside, you're on to something. Can't believe I haven't been doing this before. Thanks for showing me how stupid I am :-P

---

