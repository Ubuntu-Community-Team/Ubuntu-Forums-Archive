---
title: "Are php include tags seo friendly?"
date: 2011-02-10
forum: Programming Talk
---

### Post by Uubnewb on 2011-02-10
Are php include tags SEO friendly?  If not does anyone know of an alternative I can use?

Thanks in advance.

---

### Post by Arndt on 2011-02-10
> **Uubnewb said:**
> Are php include tags SEO friendly?  If not does anyone know of an alternative I can use?

Thanks in advance.

What does SEO friendly mean?

---

### Post by Vaphell on 2011-02-10
'search engine optimization' i guess

---

### Post by v8YKxgHe on 2011-02-10
PHP runs on the server side, your webserver will return the response of the script ran which I'm going to assume outputs HTML of some sort. I'll let you come to the conclusion here based on that information.

---

### Post by Uubnewb on 2011-02-11
Sorry for taking so long to respond.

Yes, SEO stands for Search Engin Optimization (thanks Vaphell).

AlexC, let me see if I understand this correctly:
Since the PHP include statement returns normal HTML, the bot will only see the normal HTML?

---

### Post by v8YKxgHe on 2011-02-11
> **Uubnewb said:**
> 
AlexC, let me see if I understand this correctly:
Since the PHP include statement returns normal HTML, the bot will only see the normal HTML?

Your webserver runs the PHP script, it then uses the output of said script as the response for the HTTP request. Think, if PHP was sent to the client and was ran on the client side what would you expect to see if you viewed the source code for say, [www.facebook.com?](www.facebook.com?) You'd see the PHP right?

So because you're *not* seeing the PHP code when you view the source, what does this tell you?

---

