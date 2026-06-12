---
title: "fill out web form without browser"
date: 2009-07-29
forum: Programming Talk
---

### Post by sidious1741 on 2009-07-29
I don't know much about web programming.  I actually know very little.  A week ago I didn't know any html at all.  So I'm caught with this problem.  A web site gives me a programming challenge to solve in 3 seconds (The starting data is different every time).  The page also creates a cookie.  How can I do everything a web browser can without a web browser?  What language would I use (python, html, javascript, or even C/C++)?

---

### Post by Mirge on 2009-07-30
[cURL/libcurl]("http://curl.haxx.se/") can do what you need.

---

### Post by Cyanidepoison on 2009-07-30
cURL even has a convenient command-line option to generate C code for make making a query with the command you just used with cURL, if you're planning on embedding this into something else.

---

### Post by sidious1741 on 2009-07-30
So I haven't tried anything with pycurl but here's what I have with urllib.

```
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor)
page = opener.open(page)
```

The problem is that I can't read the page because it says that I'm not logged in (I am logged in but with firefox).  What I'd like to do is to read the page and then use something like firebug where I can change the page for me the client.  Then I'm still on the same page but I can put 'javascript:void(document.forms[0].solution.value="solution");' in the code.  firebug is great but I don't know a way to write a script with firebug.  The thing is that I have to change something when I come to the page and I don't have enough time to do that.

Thanks for the help.  Unfortunately I'll be on vacation so I can't try the suggestions you've given me.  I'll post again when I come back.

---

### Post by sujoy on 2009-07-30
perl/mechanize

---

### Post by sidious1741 on 2009-08-09
I'm back from vacation.  Thanks for the help.  I figured out how to do it with urllib2.  All I did was login to the main page then go to the other page both with urllib2.  This challenge has taught me a lot.  Thanks again for the help.

---

