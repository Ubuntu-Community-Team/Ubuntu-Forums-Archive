---
title: "Python: development process"
date: 2009-03-05
forum: Programming Talk
---

### Post by blairm on 2009-03-05
Hi,

Working on my first (little) program and just want to make sure I'm going about it the right way - checked in faqs but didn't see an answer.

Trying to write something that checks news web pages and sends an email that notifies of new headlines.

Have been working on the assumption I should break the overall goal into smaller tasks (eg checking the web page every 60 minutes, writing the headlines on the page to a txt file, comparing the latest txt file with the one before and sending new material to a third file, emailing that third file with smtplib etc). 
My idea is that I ensure I can make all steps work independently before I glue them together.

Is that the correct way to go, or should I be starting at point A and moving through in order?

[EDIT] Only started playing with Python a week ago, and I had no programming experience before that.

Cheers,

Blair

---

### Post by HavocXphere on 2009-03-05
First off, I think you're heading in the wrong direction here. The more correct way to do this is with RSS feeds. If you go the downloading webpage route, then it'll put an unnecessary strain on the page's server.

I'm new to python too, so I don't know how to do the rss thing yet...

But your building blocks approach sounds right to me.

Grabbing a HTML file off the web is fairly easy. Here's a [py script I wrote last week]("https://dl.getdropbox.com/u/106416/005_DownloadFile.py") that grabs google's homepage html). The problem this is that you get a HTML file that contains all the HTML code. So you'd have to do some serious string crunching.:(

---

### Post by blairm on 2009-03-05
Thanks Havoc,

I agree, my preference would certainly be to use RSS but the feeds are terrible - they're updated irregularly, and some top stories don't seem to appear in them at all.

The info I want is all on the home page of the site and I've managed to put something together using BeautifulSoup that isolates the 10 headlines I want - the six "latest news" headlines with the publication time of each story, and the four top stories. 
Not interested in downloading the full text of the stories with the script (if the headline is enticing I'll visit the site) so I'm hoping that will minimise strain on the server.
Would also be run only 9 times a day - the hours I'm at work. 
The site has  about 1.6 million unique visitors a month, so feel a little better knowing it has a decent amount of bandwidth.

---

### Post by nvteighen on 2009-03-05
It's ok to me (apart from the RSS issue, which is not a development-related one). Good luck!

---

