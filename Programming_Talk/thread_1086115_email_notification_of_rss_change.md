---
title: "email notification of rss change?"
date: 2009-03-03
forum: Programming Talk
---

### Post by blairm on 2009-03-03
Hi,

Looking at writing some form of web scraper to monitor the latest headlines.

Almost there with one site (which has no robots.txt), but the other I'm interested in has a robots.txt file which indicates - quite fairly - that the webmaster frowns upon scraping.

That site does have an rss feed - do the same restrictions on scraping generally cover rss feeds as well? 

Considering scraping the rss page every 60 minutes while I'm at work and beng notified of new headlines by email.

(**background:** need notifications at work; our IT department refuses to install a feed reader and seems to have blocked the one in IE. They are however okay with me hosting something on one of my computers and using email notifications of new headlines).

Blair

---

### Post by cabalas on 2009-03-03
What about a web based feed reader like [google reader]("http://reader.google.com")? would that not do the trick

---

### Post by G|N| on 2009-03-04
You could use the new version from specto ([http://specto.sf.net](http://specto.sf.net))...
It is able to monitor webpages and you can define a custom command when the webpage is updated (so sending you the email using sendemail)

---

### Post by rdingram on 2009-03-09
Check out rss2email. If you set it up as a cron job it will email you when a new rss post is out.

you can install by doing 

```
sudo apt-get install rss2email
```

---

### Post by wmcbrine on 2009-03-09
> **blairm said:**
> That site does have an rss feed - do the same restrictions on scraping generally cover rss feeds as well?No, that's kind of the whole point of RSS (i.e., to make it easier for machines to access the content). Reading an RSS feed is not "scraping". Not that I agree that a webmaster trying to prohibit screen scraping is being "fair", or that that's anything you should pay attention to. Also, I suspect that someone saying "don't screen scrape", and simultaneously offering an RSS feed, may not know what he's doing. Unless he's saying, "Look, we have this nice RSS feed over here, you don't need to scrape."

Are you sure it wasn't about hot-linking rather than scraping? That would make more sense.

---

