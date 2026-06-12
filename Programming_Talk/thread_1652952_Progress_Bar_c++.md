---
title: "Progress Bar c++"
date: 2010-12-25
forum: Programming Talk
---

### Post by roadkillguy on 2010-12-25
Hi, I'm trying to write a progress bar into my c++ application. I'm loading a great deal of data, and it takes a long time to load.  How would I make a progress bar run alongside the for loop loading all the data?

I'd like to avoid updating every x iterations of the loop. (That would only make it slower)

Thanks for the help.

---

### Post by worksofcraft on 2010-12-26
This is a very worthwhile question... Many programs only show an "activity" indicator. Sometimes a spinner, or even some kind of bar graph but it just keeps filling regardless if any progress is being made and when it reaches the end it simply starts all over again... e.g. try unplugging your modem and just watch Internet Explorer merrily keep filling the progress bar :shock:

So what you need to be able to do is calculate the total extent of processing... whatever that may be... before you start and then have some kind of indicator that is proportional to the progress being made.

Say you are copying files, well you could stat them all first and get all their sizes and then keep track of how much data you have copied to update said indicator. However you see it involves some up front processing to workout your total!

There will however be many processes that you simply cannot know how long they will take until you've actually done completed them!

---

### Post by nvteighen on 2010-12-26
You'll need to use parallel programming: I think executing the progress bar function in a separate thread will do it right. Take a look at this guide: [https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

---

