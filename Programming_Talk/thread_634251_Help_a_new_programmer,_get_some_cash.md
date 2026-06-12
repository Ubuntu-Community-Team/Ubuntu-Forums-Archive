---
title: "Help a new programmer, get some cash?"
date: 2007-12-07
forum: Programming Talk
---

### Post by lapubell on 2007-12-07
Hello all.  I am a fairly new programmer that works mostly with server side web programming.  I'm not too familiar with desktop app programming, but I have done some work with the wxWidgets and python (nothing very impressive, just a simple text editor with a whole bunch of bugs).

In my web development projects I have come across the demand for a large website needing to have a RSS feed checker made.  They are a real estate website that receives feeds from many, MANY, different sources and most of the time there is a syntax error, of a string where there should be an int, things like that.

I came up with an original proposed idea, a site with three steps. 1) Point us to your feed, 2) Run a php (or maybe python now) script to catch the errors, and 3) return with a line number error report.  This seemed simple enough to me at first, but then I started to dig a little deeper and realized that this is actually going to be tougher than I thought.  What changed is that the company said they get sent feeds that are up to 250MB (on the larger side, the average is about 20MB to 60MB).

So here is my new idea.  Write a python script that runs the test.  Use that on the site, and also inside of a desktop app.  If the feed is larger than a number that we pick, say five megs, then the website would instruct them to download the desktop app and check it that way.  I was thinking wx with python because I have done it before and we could make binaries to run on any platform (most of these users would be running windows, unfortunately).

So is anyone out there willing to team up on a new open source project?  I have a commission coming my way, if it fits their budget and we can work the deadlines, and I would be more than willing to take a smaller cut to learn some good coding practices.  I'm not sure if we should talk over the forums about a specific project, so reply to this if you know you are up to this project and then we can find other ways of communicating.

Thanks and I look forward to hearing from some excited programmers!

---

