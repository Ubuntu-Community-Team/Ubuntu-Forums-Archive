---
title: "Retrieving book information in C++. Which libary/service/etc?"
date: 2006-12-24
forum: Programming Talk
---

### Post by veraction on 2006-12-24
I'm writing a small app for myself in C++, and I want to implement a feature which primarily will retrieve basic book information (e.g., title and author) based on a given ISBN. 

**I'm seeking advice on which libraries/tools/services to use, or any open-source applications which might do something similar to this (especially related to C/C++)**. I haven't worked with web services using SOAP, but I have a general idea of how it works.

I've found Alexandria, which is open source and written in ruby. I think this is a decent starting point, and I'll be looking into it. 

I've looked at Amazon AWS some. I didn't see any examples using C or C++. I saw one which used PHP, but it didn't seem to work (even had spelling errors all over). I saw another one for Perl, but I haven't used Perl, nor does it seem to work after I got SOAP::Lite

[http://koders.com](http://koders.com) and [http://google.com/codesearch](http://google.com/codesearch) haven't yielded any results, but maybe my search terms were wrong (using C or C++)

---

### Post by po0f on 2006-12-24
veraction,

You can probably get C(++) to parse output from a query to [the Library of Congress](http://www.loc.gov/index.html) or Amazon.com.  I haven't done much WWW programming, so I can't really recommend any specific libraries to you, though I hear quite a bit about Python/BeautifulSoup.

---

