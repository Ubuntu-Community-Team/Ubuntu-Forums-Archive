---
title: "Should I reinvent the wheel?"
date: 2009-03-06
forum: Programming Talk
---

### Post by blairm on 2009-03-06
Trying to write my first reasonable(for me) program. Want an email alert when an rss feed has been updated,
The more I think of it, the more I think I have three options: which is likely to be the easiest for a beginner? Ot am I missing something obvious?

1) write a python script that scrapes the home page using BeautifulSoup to grab the bits I want and smtplib to send a notification email when the feed is updated.

2) take an existing feed reader eg thunderbird and try to get an email sent when new rss items show via dbus (not 100% this is possible, but haven't seen anything to say it isn't yet)

3)find a newsreader written in python and add a few lines to the code to send an email via smtplib when a rss feed is updated.

Until a week ago I hadn't played much with programming, so I'm an absolute amateur.

Any advice much appreciated,

Blair

---

### Post by mirons on 2009-03-06
Hi, here's a computer science student's opinion:
if you want something that work in a reasonable time try option 1.
if you want to learn better programming try option 3, but be conscious that looking other people code will take you lot of time (then it depends on the quality of comment/design). Things in big programs are generally complex in order to be flexible.

---

### Post by albandy on 2009-03-06
as rss is xml you can program it in a very easy way with java and jdom

---

### Post by wmcbrine on 2009-03-06
> **albandy said:**
> as rss is xml you can program it in a very easy way with java and jdomOr with Python, as seems to be the OP's preference.

Yes, all the proposed solutions are overkill. You can grab and parse an RSS feed in just a few lines of Python (then send the message with smtplib, I guess). No screen scraping needed, no need no modify an existing feed reader.

---

### Post by blairm on 2009-03-06
Thanks for everyone's advice.

Have got something working using wmcbrine's advice - at least to a point where it outputs the links, headlines and first paragraph of stories in the feed. Hadn't thought of doing it that way:oops: 

Now I just have to work out how to add smtplib to email that output ... lucky I've got a three day weekend!

Blair

---

### Post by kavon89 on 2009-03-06
These days, everyone is "reinventing the wheel" when it comes to applications. Almost every idea for a program that solves a general problem or simplifies a task has already been done. It is more or less a competition to see who can do it the best at the lowest price (if any).

---

