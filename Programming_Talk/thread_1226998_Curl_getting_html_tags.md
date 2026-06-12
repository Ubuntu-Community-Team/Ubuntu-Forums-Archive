---
title: "Curl getting html tags"
date: 2009-07-30
forum: Programming Talk
---

### Post by aliahsan81 on 2009-07-30
I am making a script in which i wana use curl to download a web page and check status.But problem is when i use curl in linux command line it downlaod htlm tags.How can we ignore these tage any idea.

---

### Post by v8YKxgHe on 2009-07-30
You just want the response headers?
```
curl -I http://example.com
```

---

### Post by aliahsan81 on 2009-07-30
Thanks for quick reply.

I want to get page content to parse in my script.

---

### Post by v8YKxgHe on 2009-07-30
> **aliahsan81 said:**
> Thanks for quick reply.

I want to get page content to parse in my script.

What you get from CURL is the page content, you're getting the document returned from the server - which I assume is an HTML document, so of course it will have the HTML markup in it.

---

### Post by aliahsan81 on 2009-07-30
yes correct so there is some way i can remove these html tags

---

### Post by Mirge on 2009-07-30
If using PHP, you can use [strip_tags()]("http://us3.php.net/strip_tags/")..

---

