---
title: "monitoring changes in web page with python"
date: 2009-03-02
forum: Programming Talk
---

### Post by blairm on 2009-03-02
Hi,

Have been playing with Python/Beautiful Soup for a couple of days and have written something to get all the headlines from a news web site's home page.

What I'd like to do now is extend what I've written so the site is scraped every 60 minutes, and an email is sent if the headlines have changed.

The email part looks reasonably straightforward, but I'm unsure how to proceed re comparing the headline files. 
Google hasn't been a great help; I've found a lot of programs that do what I want (eg Specto, ScreenScraper), but want to make my own as a learning experience.

Is anyone able to provide some indication on how I should approach this? Please note I'm not after anyone to do this for me, because I'm stubborn and want to solve this.
But a hint on what the best method might be would be much appreciated.

Thanks,

Blair

---

### Post by rharriso on 2009-03-02
Well just off the cuff. I would say if you were running this as a cron job, to have the program store the headlines into a file then read them into an array when the program starts up, then compare all new headlines to that array, if its not in there, you know its new.

---

### Post by blairm on 2009-03-03
Many thanks for your help. Finding python a lot of fun... think I might have discovered a new hobby!

Blair

---

