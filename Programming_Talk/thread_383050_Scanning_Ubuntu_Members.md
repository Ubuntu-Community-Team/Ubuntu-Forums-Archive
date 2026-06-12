---
title: "Scanning Ubuntu Members"
date: 2007-03-12
forum: Programming Talk
---

### Post by phossal on 2007-03-12
If you scan the source of the Ubuntu Forums home page while it's really busy, you can look for these lines:

*[COLOR="DimGray"]<a href="member.php?u=147443" rel="nofollow">phossal</a>[/COLOR]*

With a little perl (or python) magic, you can see who (theoretically) joined when. It's interesting.

---

### Post by maddog39 on 2007-03-12
Well basically you would have to import and parse the HTML and filter out all the junk then filter the table with the data and then support vB pagination. Possible but a pain.

---

### Post by jdong on 2007-03-13
Yeah, "website scraping" -- it can definitely be a fun thing to do, and also a good challenge in learning the string manipulation capabilities of your language.

One thing I will say, scrapers tend to cause many times the workload to the server than a human browsing, so please be considerate. Limit your request rate to something that a human would likely do. If it's a long-term program, cache copies of pages that would not likely change (i.e. the join date of a particular member would only need to be fetched once and stored)

---

### Post by phossal on 2007-03-13
It isn't really a project I was going to make available. I did it one time, with very little effort and a few lines of perl, by saving the source while I was logged in to the page. I found it surprising that the data is "hard coded" into the page more than anything.

Regards.

---

