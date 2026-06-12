---
title: "bash script to automate web search (eg for airline flights)."
date: 2012-04-25
forum: Programming Talk
---

### Post by F.G. on 2012-04-25
hey folks,

so, a friend of mine recommended a utility to find cheap flights (called azuon) and it got me to thinking, how would you write a script to automate looking up stuff (in this case filghts) on the internet?

my thoughts were to have a file with a list websites in (ryanair, easyjet, etc) and a folder with a bunch of model web pages(copied from the websites) and iteratively curl http requests, filling in the various fields with command line variables. then order the results.

however, this seems like a really messy way to attempt something like this, does anyone have any suggestions for a better way?

thanks for all replies

---

### Post by cmont899 on 2012-04-25
A lot of travel sites have RSS feeds available for ticket pricing, this may be easier than curl/expect-fu that would have to constantly be edited as sites update their UI.

---

### Post by F.G. on 2012-04-25
thanks for the suggestion, that would probably be a better way to do this specific task, particularly as i guess a lot of rss readers have search functionality, so, i could probably just use something like liferea of whatever and get decent results. i don't know what command line rss readers there are for ubuntu, although there must be a few.

however that still wouldn't actually allow you to submit http requests to query the websites db? (as far as i'm aware rss feeds are a one way thing?). anyhow that certainly could be a solution.

---

### Post by LemursDontExist on 2012-04-28
curl is problematic here.  

The biggest problem is a lot of these airfare search sites authenticate your search session server-side after setting cookies.  As a result you can't just send an http request and hope to get data back.  Generating the requisite http requests complete with session cookies is far from trivial, especially since the cookies are sometimes set via javascript rather than being transmitted the old-fashioned way.

If you just want to get data from a small handful of specific airlines, it might not be too bad, but this project is a lot harder than you might think!

---

